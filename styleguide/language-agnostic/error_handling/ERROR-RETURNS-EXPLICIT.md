---
type: Styleguide Rule
description: |-
  Functions that can fail should make this obvious in return type and
  documentation. Don't hide failure modes.
language: language-agnostic
category: error_handling
rule_id: ERROR-RETURNS-EXPLICIT
priority: error
tags:
- errors
- documentation
- contracts
---
Functions that can fail should make this obvious in return type and
documentation. Don't hide failure modes.

## Good

- // Returns NULL on failure
Entity* FindEntity(int id);
- // Returns error code, 0 on success
int Connect(address);

## Bad

- Entity* FindEntity(int id); // What if not found?
