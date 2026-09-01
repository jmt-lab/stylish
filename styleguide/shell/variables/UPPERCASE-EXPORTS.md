---
type: Styleguide Rule
description: Use UPPERCASE for environment variables and exports, lowercase for local variables.
language: shell
category: variables
rule_id: UPPERCASE-EXPORTS
priority: info
tags:
- variables
- naming
- environment
---
Use UPPERCASE for environment variables and exports, lowercase for local variables.

## Good

- export PATH="/usr/local/bin:${PATH}"
- export DATABASE_URL="postgres://localhost"
- local temp_file='/tmp/data'

## Bad

- export path="/usr/local/bin:${path}"
- local TEMP_FILE='/tmp/data'  # Local shouldn't be uppercase
