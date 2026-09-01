---
type: Styleguide Rule
description: Quote special variables like $@, $*, and understand $?, $#, $$, $!, $0.
language: shell
category: variables
rule_id: SPECIAL-VAR-HANDLING
priority: error
tags:
- variables
- special
- arguments
---
Quote special variables like $@, $*, and understand $?, $#, $$, $!, $0.

## Good

- main "$@"  # Pass all arguments preserving spaces
- if [[ $? -eq 0 ]]; then  # Check exit status
- echo "Script: $0, Args: $#"

## Bad

- main $@  # Breaks with spaces in arguments
- if [[ ${?} -eq 0 ]]; then  # Unnecessary braces
