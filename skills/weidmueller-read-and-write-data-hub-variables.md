---
generated: '2026-10-09'
method: generated
name: read-and-write-data-hub-variables
description: Discover Data Hub providers on a Weidmüller u-OS device and read or write their variable values over the Variable-HTTP API.
api: openapi/weidmueller-variable-http-openapi.yml
operations: [get_providers_handler, get_variables_handler, get_single_variable_handler, post_single_variable_handler, post_multiple_variables_handler]
source: Grounded in openapi/weidmueller-variable-http-openapi.yml (from github.com/weidmueller/u-os-hub-api). Every operationId verified verbatim in the spec.
---

# Read and write Data Hub variables

## Auth
- OAuth2 client credentials against the device's `/oauth2/token`. Scope `hub.variables.readonly` to read, `hub.variables.readwrite` to write.
- Base path on the device: `/u-os-hub/api/v1`.

## Steps
1. **List providers**: `get_providers_handler` (`GET /providers`). Pick the `provider_id`.
2. **Read all variables of a provider**: `get_variables_handler` (`GET /providers/{provider_id}/variables`).
3. **Read one variable**: `get_single_variable_handler` (`GET /providers/{provider_id}/variables/{variable_key}`).
4. **Write one variable**: `post_single_variable_handler` (`POST /providers/{provider_id}/variables/{variable_key}`). Needs `hub.variables.readwrite`.
5. **Write several variables at once**: `post_multiple_variables_handler` (`POST /providers/{provider_id}/variables`).

## Rules
- Writes change live values on an industrial device. Read the current value first and confirm before you write.
- For change notifications, use the Variable-NATS API (asyncapi/weidmueller-variable-nats-asyncapi.yml), not polling.
