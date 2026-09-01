---
type: Styleguide Rule
description: |-
  When code changes, update comments. Stale comments are worse than
  no comments as they mislead future readers.
language: rust
category: comments
rule_id: UPDATE-STALE-COMMENTS
priority: error
tags:
- maintenance
- accuracy
- carmack
---
When code changes, update comments. Stale comments are worse than
no comments as they mislead future readers.

## Bad

- /// Returns true if valid
fn check_entity(&self) -> &Entity // Returns entity, not bool!
