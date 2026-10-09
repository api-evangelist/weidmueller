---
generated: '2026-10-09'
method: generated
name: generate-a-log-report
description: Trigger and download a system log report from a Weidmüller u-OS device, polling the long-running operation until it finishes.
api: openapi/weidmueller-administration-openapi.yml
operations: [get_logging_sources, get_logging_entries, create_logging_report, get_operation, get_logging_report]
source: Grounded in openapi/weidmueller-administration-openapi.yml (from github.com/weidmueller/u-os-hub-api). Every operationId verified verbatim in the spec.
---

# Generate a log report

## Auth
- OAuth2 client credentials (`/oauth2/token` on the device), scope `u-os-adm.logging.readonly`. Base path `/u-os-adm/api/v1`.

## Steps
1. Optional: list sources with `get_logging_sources` (`GET /logging/sources`) or read entries directly with `get_logging_entries` (`GET /logging/entries`).
2. **Start the report**: `create_logging_report` (`POST /logging/reports`). It returns 202 because this is a long-running operation. A 409 means a report generation conflicts with one already running.
3. **Poll**: `get_operation` (`GET /operations/{operation_id}`) until it completes. The spec notes that the operation ID can only be retained when the operation is created, so keep it.
4. **Download**: `get_logging_report` (`GET /logging/reports/{report_id}`) returns a gzipped tar archive of the system logs.
