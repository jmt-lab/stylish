---
type: Styleguide Rule
description: |-
  Do not capitalize error strings (unless they start with an exported name,
  proper noun, or acronym) and do not end them with punctuation; they are
  usually embedded in other messages. Full log and UI messages are typically
  capitalized.
language: go
category: error_handling
rule_id: ERROR-STRINGS-LOWERCASE
priority: warn
tags:
- errors
- messages
- google-style
---
Do not capitalize error strings (unless they start with an exported name,
proper noun, or acronym) and do not end them with punctuation; they are
usually embedded in other messages. Full log and UI messages are typically
capitalized.

## Good

- err := fmt.Errorf("something bad happened")
- log.Errorf("Operation aborted: %v", err)

## Bad

- err := fmt.Errorf("Something bad happened.")
- errors.New("Failed to connect!")
