---
generated: '2026-10-09'
method: generated
name: inspect-device
description: Check that a Weidmüller u-OS device is up and read its system info, digital nameplate and disks.
api: openapi/weidmueller-administration-openapi.yml
operations: [ping, get_system_info, get_system_nameplate, get_system_disks]
source: Grounded in openapi/weidmueller-administration-openapi.yml (from github.com/weidmueller/u-os-hub-api). Every operationId verified verbatim in the spec.
---

# Inspect a u-OS device

## Steps
1. `ping` (`GET /ping`) verifies that the backend has started.
2. `get_system_info` (`GET /system/info`) returns static system information.
3. `get_system_nameplate` (`GET /system/nameplate`) returns the digital nameplate.
4. `get_system_disks` (`GET /system/disks`) returns disk information.

## Auth
- OAuth2 client credentials (`/oauth2/token` on the device). Base path `/u-os-adm/api/v1`. Check each operation's security requirement in the spec for the scope it needs.
