---
type: Styleguide Rule
description: Declare constants with readonly (or declare -r) to prevent accidental modification and make intent explicit.
language: shell
category: features
rule_id: READONLY-FOR-CONSTANTS
priority: warn
tags:
- constants
- immutability
- safety
---
Declare constants with readonly (or declare -r) to prevent accidental modification and make intent explicit.

## Good

- readonly MAX_RETRIES=3
- readonly CONFIG_FILE="/etc/app/config"
- declare -r PI=3.14159

## Bad

- MAX_RETRIES=3  # Can be accidentally changed
- CONFIG_FILE="/etc/app/config"  # Mutable
