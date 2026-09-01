---
type: Styleguide Rule
description: Add comments to explain non-obvious logic, especially complex conditionals or regex patterns.
language: shell
category: comments
rule_id: EXPLAIN-COMPLEX
priority: warn
tags:
- comments
- clarity
---
Add comments to explain non-obvious logic, especially complex conditionals or regex patterns.

## Good

- # Match IPv4 addresses in CIDR notation
if [[ "${ip}" =~ ^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}/[0-9]{1,2}$ ]]; then


## Bad

- if [[ "${ip}" =~ ^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}/[0-9]{1,2}$ ]]; then

