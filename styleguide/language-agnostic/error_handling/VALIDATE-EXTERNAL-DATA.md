---
type: Styleguide Rule
description: |-
  Never trust external data (files, network, user input). Validate
  thoroughly before use.
language: language-agnostic
category: error_handling
rule_id: VALIDATE-EXTERNAL-DATA
priority: error
tags:
- validation
- security
- safety
---
Never trust external data (files, network, user input). Validate
thoroughly before use.

## Good

- if (size > MAX_SIZE || size < 0) {
    return ERROR_INVALID;
}

## Bad

- buffer = malloc(size); // No validation of size
