---
type: Styleguide Rule
description: |-
  Keep side effects (I/O, global state changes) at system boundaries.
  Core logic should be pure functions that transform data.
language: language-agnostic
category: functional_patterns
rule_id: SIDE-EFFECT-ISOLATION
priority: warn
tags:
- side-effects
- architecture
- purity
---
Keep side effects (I/O, global state changes) at system boundaries.
Core logic should be pure functions that transform data.

## Good

- // Pure core
Result Process(Data d) { ... }
// Side effects at boundary
void Main() {
    data = ReadFile();
    result = Process(data);
    WriteFile(result);
}

## Bad

- Result Process(Data d) {
    // Mixed I/O with logic
    WriteLog();
    ... logic ...
    UpdateGlobal();
}
