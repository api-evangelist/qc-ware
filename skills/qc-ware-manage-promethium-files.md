---
name: qc-ware-manage-promethium-files
description: Upload, organize, retrieve and delete molecular input and output files in a QC Ware Promethium account's file tree.
api: Promethium REST API
base_url: https://api.promethium.qcware.com
operations:
  - list_files
  - create_file
  - create_file_batch
  - get_file
  - update_file
  - delete_file
  - download_file
generated: '2026-08-26'
method: generated
source: openapi/qc-ware-promethium-openapi.yml
---

# Manage Promethium files

Every operation requires the header `X-API-KEY: <your Promethium API key>`.

The Promethium file store is a **self-referential tree**. A `FileMetadata` node is either a file or a
directory (`is_directory`), and every node except the root carries a `parent_id` pointing at its directory.

## Upload a file

`POST /v0/files` (`create_file`) → **201**. The body is one of two shapes:

- `CreateSimpleFileRequest` — `{"name": "...", "base64body": "<base64>", "parent_id": "<uuid4>"}`.
  `is_directory` is pinned to `false`. `name` and `base64body` are required.
- `CreateDirectoryRequest` — `{"name": "...", "parent_id": "<uuid4>"}`. `is_directory` is pinned to `true`.

For several files at once use `POST /v0/files/batch` (`create_file_batch`), which takes an **array** of the
same two shapes. There is no batch delete and no batch rollback — if a batch half-fails you must clean up
per file.

## Browse

`GET /v0/files` (`list_files`) with:
- `parent_id` — list the children of one directory. Omit it to list from the root.
- `search` — name search.
- `page` (min 1) and `size` (min 1) — the response is a `Page_FileMetadata_` envelope with
  `items`, `total`, `page`, `size`.

`GET /v0/files/{file_id}` (`get_file`) returns one node's metadata, including
`size_bytes_uncompressed` and `sha256_uncompressed` — use the SHA-256 to verify an upload rather than
re-downloading it.

## Move

`PATCH /v0/files/{file_id}` (`update_file`). The **only** mutable field is `parent_id` — this operation is a
move, not a rename and not a content update. It is self-inverse: PATCH it back to restore the previous
location. The API does **not** return the prior `parent_id`, so capture it with `get_file` *before* moving,
or you cannot undo.

## Download

`GET /v0/files/{file_id}/download` (`download_file`) → **302** redirect to the file content. Follow the
redirect.

## Delete — irreversible

`DELETE /v0/files/{file_id}` (`delete_file`) → **204**.

There is **no restore, undelete, trash or recovery-window operation** in the published contract. Once
deleted, a file is gone as far as the API is concerned. Confirm with `get_file` and, for anything that took
GPU time to produce, download it before deleting.

## Errors

Only **422** is declared, with the FastAPI `{"detail":[{"loc","msg","type"}]}` envelope. A wrong `file_id`
will not produce that shape — 404 is undeclared. Handle by status code.
