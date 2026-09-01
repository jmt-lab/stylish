---
type: Styleguide Rule
description: Declare all constants and configuration near the top of the script after the header.
language: shell
category: organization
rule_id: CONSTANTS-AT-TOP
priority: warn
tags:
- organization
- constants
---
Declare all constants and configuration near the top of the script after the header.

## Good

- #!/bin/bash

readonly MAX_RETRIES=3
readonly TIMEOUT=30
readonly CONFIG_DIR="/etc/app"

main() { ... }


## Bad

- #!/bin/bash

main() {
  readonly MAX_RETRIES=3  # Don't define in functions
  ...
}

