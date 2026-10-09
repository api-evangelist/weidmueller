---
generated: '2026-10-09'
method: generated
name: update-network-configuration
description: Inspect and modify a Weidmüller u-OS device's network configuration with a JSON merge patch, then verify the resulting state.
api: openapi/weidmueller-administration-openapi.yml
operations: [get_network_config, update_network_config, get_network_state]
source: Grounded in openapi/weidmueller-administration-openapi.yml (from github.com/weidmueller/u-os-hub-api). Every operationId verified verbatim in the spec.
---

# Update network configuration

## Auth
- OAuth2 client credentials. Scopes `u-os-adm.network.readonly` and `u-os-adm.network.readwrite`. Base path `/u-os-adm/api/v1`.

## Steps
1. `get_network_config` (`GET /network/config`) reads the current configuration.
2. `update_network_config` (`PATCH /network/config`) applies a JSON merge patch (RFC 7396) to the current configuration and returns the updated configuration.
3. `get_network_state` (`GET /network/state`) confirms the live state.

## Rules
- Changing the address of the interface you are connected through can drop the session. Confirm with a human first.
