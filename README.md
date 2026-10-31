# QC Ware

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

QC Ware is a quantum and GPU-accelerated computational chemistry company based in Palo Alto, California. Its commercial product is Promethium, a cloud-native quantum chemistry platform that runs ab initio DFT and TD-DFT calculations on NVIDIA A100/V100 GPUs for systems up to roughly 2,000 atoms, used by pharmaceutical and materials-science discovery teams. Promethium exposes a public REST API at api.promethium.qcware.com covering workflow submission (single point, geometry optimization, conformer search, torsion scan, interaction energy / F-SAPT, reaction path and transition state optimization) and a file/project store, plus a Python SDK and a `promethium`/`pm` command-line tool. QC Ware also ran Forge, an earlier quantum computing cloud service with a Python client library, and hosts the Q2B quantum computing conference series.

**Areas:** Company · Quantum Computing · Computational Chemistry · Quantum Chemistry · Drug Discovery · Materials Science · Scientific Computing · GPU Computing · Life Sciences · Simulation

## QC Ware on APIs.io

Everything profiled for QC Ware is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/qc-ware/](https://apis.io/providers/qc-ware/)** — or go straight to one of the APIs or properties below.

### APIs (2)

- [QC Ware Files API](https://apis.io/apis/qc-ware/qc-ware-files-api/) — The Files API from QC Ware — 4 operation(s) for files.
- [QC Ware Workflows API](https://apis.io/apis/qc-ware/qc-ware-workflows-api/) — The Workflows API from QC Ware — 5 operation(s) for workflows.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [qc-ware-mcp.yml](https://apis.io/servers/qc-ware/qc-ware-mcp-yml/)

#### Examples (3)

Example requests and responses.

- [Qc Ware Conformer Search Request](https://apis.io/examples/qc-ware/qc-ware-conformer-search-request/)
- [Qc Ware Geometry Optimization Request](https://apis.io/examples/qc-ware/qc-ware-geometry-optimization-request/)
- [Qc Ware Single Point Calculation Request](https://apis.io/examples/qc-ware/qc-ware-single-point-calculation-request/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Qc Ware Promethium Overlay](https://apis.io/overlays/qc-ware/qc-ware-promethium-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Qc Ware Authentication](https://apis.io/security/qc-ware/qc-ware-authentication/)
- [Qc Ware Domain Security](https://apis.io/security/qc-ware/qc-ware-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Qc Ware Plans Pricing](https://apis.io/plans/qc-ware/qc-ware-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Qc Ware Rate Limits](https://apis.io/rate-limits/qc-ware/qc-ware-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.qcware.com/)
- [Documentation](https://github.com/qcware/promethium-examples)
- [Getting started](https://github.com/qcware/promethium-examples#getting-started-with-the-promethium-api--software-development-kit-sdk)
- [API reference](https://app.promethium.qcware.com/docs/api)
- [Pricing](https://www.promethium.qcware.com/pricing-details)
- [Sign up](https://app.promethium.qcware.com/)
- [Support](https://www.promethium.qcware.com/contact)
- [Blog](https://www.promethium.qcware.com/blog)
- [Privacy policy](https://www.qcware.com/privacy/privacy-policy)
- [GitHub](https://github.com/qcware)
- [Status](https://promethium-status.qcware.com/)

## API Evangelist rating

**Kin Score 53.0** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 49.0 |
| Contract governance | 4.5 |
| Operational transparency | 18.4 |
| Developer ergonomics | 73.2 |
| Access clarity | 73.7 |

**Agent readiness 29.9** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 24.2** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/qc-ware/](https://apis.io/providers/qc-ware/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for QC Ware: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/qc-ware/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
