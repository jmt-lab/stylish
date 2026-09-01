---
type: Styleguide Rule
description: |-
  When code changes, update comments. Stale comments are worse than
  no comments as they mislead future readers.
language: language-agnostic
category: comments
rule_id: UPDATE-STALE-COMMENTS
priority: error
tags:
- maintenance
- accuracy
- hygiene
---
When code changes, update comments. Stale comments are worse than
no comments as they mislead future readers.

## Bad

- // Returns true if valid
return entity; // Returns entity, not bool
