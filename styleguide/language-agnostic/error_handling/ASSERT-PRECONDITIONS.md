---
type: Styleguide Rule
description: |-
  Every function should assert its preconditions at the start. This
  catches contract violations immediately at the call site.
language: language-agnostic
category: error_handling
rule_id: ASSERT-PRECONDITIONS
priority: error
tags:
- assertions
- preconditions
- contracts
---
Every function should assert its preconditions at the start. This
catches contract violations immediately at the call site.

## Good

- void Process(Entity* entity) {
    assert(entity != NULL);
    assert(entity->IsValid());
}

## Bad

- void Process(Entity* entity) {
    // Hope entity is valid
    entity->Update();
}
