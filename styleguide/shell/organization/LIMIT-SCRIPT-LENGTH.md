---
type: Styleguide Rule
description: If a script grows too large (>500 lines), consider splitting into multiple scripts or sourcing libraries.
language: shell
category: organization
rule_id: LIMIT-SCRIPT-LENGTH
priority: info
tags:
- organization
- maintainability
---
If a script grows too large (>500 lines), consider splitting into multiple scripts or sourcing libraries.

## Good

- #!/bin/bash
source lib/common.sh
source lib/validation.sh

main() { ... }


## Bad

- # 2000 line monolithic script
