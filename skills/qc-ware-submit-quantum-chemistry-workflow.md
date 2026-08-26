---
name: qc-ware-submit-quantum-chemistry-workflow
description: Submit a GPU quantum chemistry calculation to QC Ware Promethium and retrieve its results, without double-billing or losing track of a running workflow.
api: Promethium REST API
base_url: https://api.promethium.qcware.com
operations:
  - create_workflow
  - get_workflow
  - get_workflow_results_numeric
  - download_results
  - stop_workflow
generated: '2026-08-26'
method: generated
source: openapi/qc-ware-promethium-openapi.yml + https://github.com/qcware/promethium-examples
---

# Submit a Promethium quantum chemistry workflow

Every operation requires the header `X-API-KEY: <your Promethium API key>`. Keys are created on the API tab
of https://app.promethium.qcware.com/settings/.

## Before you submit — read this first

`create_workflow` starts metered GPU compute. There is **no idempotency key** on this API and **no dry-run
mode**. If a submission times out at the network layer, do **not** retry it: call `list_workflows` with the
`kind` you submitted and check whether your `name` is already there. Retrying blind starts a second billed
workflow.

## Steps

1. **Choose the workflow kind.** It must be one of the eight `UnifiedWorkflowKind` values:
   `SinglePointCalculation`, `GeometryOptimization`, `ConformerSearch`, `TorsionScan`,
   `InteractionEnergyCalculation`, `ReactionPathOptimization`, `TransitionStateOptimization`,
   `TransitionStateOptimizationFromEndpoints`.

2. **Build the request body.** `create_workflow` takes `CreateWorkflowRequest`:
   - `name` (required) — your own label for the run.
   - `kind` (required) — from step 1.
   - `parameters` (required) — **the OpenAPI types this as a bare `object` with no sub-schema.** Its real
     shape differs per kind. Copy a working shape from `examples/` in this repo, or from
     https://github.com/qcware/promethium-examples. A molecule is normally passed as
     `{"molecule": {"base64data": "<base64 XYZ>", "filetype": "xyz"}}`.
   - `resources` (required) — `{"gpu_type": "a100" | "v100", "gpu_count": <int, default 1>}`.
   - `version` — defaults to `"v1"`.

3. **Submit.** `POST /v0/workflows` (`create_workflow`). A success is **201**, and the body is a `Workflow`
   carrying `id` (uuid4), `status`, `created_at` and your echoed `parameters`. Record the `id` immediately —
   it is the only handle you will get.

4. **Poll.** `GET /v0/workflows/{workflow_id}` (`get_workflow`). Statuses run
   `SUBMITTED → PENDING → RUNNABLE → STARTING → RUNNING` and then reach a terminal value:
   `SUCCEEDED`, `COMPLETED`, `CANCELED`, `FAILED`, `TERMINATED` or `TIMED_OUT`.
   There is no webhook and no event stream — polling is the only completion signal QC Ware publishes.
   No rate limits are documented, so poll at a sane interval and back off on any non-2xx.

5. **Read results.** On a terminal success:
   - `GET /v0/workflows/{workflow_id}/results` (`get_workflow_results_numeric`) → numeric results inline.
   - `GET /v0/workflows/{workflow_id}/results/download` (`download_results`) → **302** redirect to the full
     archive. Follow the redirect; do not treat the 302 as an error.

6. **Abort if needed.** `POST /v0/workflows/{workflow_id}/stop` (`stop_workflow`) → **204**.
   QC Ware publishes **no window** for this and **no statement about whether elapsed compute is still
   billed**. Stop early rather than late, and do not assume a refund.

## Errors

The only declared error response is **422**, with a FastAPI envelope:
`{"detail": [{"loc": [...], "msg": "...", "type": "..."}]}`. Read `detail[].loc` to find the bad field.

401, 403, 404, 429 and 5xx are **not declared** in the contract even though the API can return them. Handle
them defensively by status code; do not code against an assumed body shape.
