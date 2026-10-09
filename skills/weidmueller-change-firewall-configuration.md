---
generated: '2026-10-09'
method: generated
name: change-firewall-configuration
description: Safely change a Weidmüller u-OS device firewall by testing a temporary active override before you persist it.
api: openapi/weidmueller-administration-openapi.yml
operations: [get_firewall_config, get_firewall_active_config, update_firewall_active_config, reload_firewall_config, update_firewall_config]
source: Grounded in openapi/weidmueller-administration-openapi.yml (from github.com/weidmueller/u-os-hub-api). Every operationId verified verbatim in the spec.
---

# Change firewall configuration

## Auth
- OAuth2 client credentials. Scope `u-os-adm.firewall.readonly` to read, `u-os-adm.firewall.readwrite` to change. Base path `/u-os-adm/api/v1`.

## Steps
1. Read the persistent config with `get_firewall_config` (`GET /firewall/config`) and the active one with `get_firewall_active_config` (`GET /firewall/active-config`).
2. **Try the change temporarily**: `update_firewall_active_config` (`PATCH /firewall/active-config`). This sets a temporary override.
3. **Roll back if needed**: `reload_firewall_config` (`POST /firewall:reload`) deletes the temporary config and reloads the persistent one. It does nothing when no temporary config is active.
4. **Persist**: `update_firewall_config` (`PATCH /firewall/config`) once the change is confirmed.

## Rules
- A bad firewall rule can lock the agent out of the device. Always test with the temporary override first.
