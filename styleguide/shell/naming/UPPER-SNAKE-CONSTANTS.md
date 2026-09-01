---
type: Styleguide Rule
description: Constants and exported environment variables should be uppercase with underscores.
language: shell
category: naming
rule_id: UPPER-SNAKE-CONSTANTS
priority: error
pattern: ^[A-Z][A-Z0-9_]*$
tags:
- naming
- constants
- environment
---
Constants and exported environment variables should be uppercase with underscores.

## Good

- readonly MAX_RETRIES=3
- export PATH_TO_FILES='/tmp'

## Bad

- readonly maxRetries=3
- export pathToFiles='/tmp'
