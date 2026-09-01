---
type: Styleguide Rule
description: "Do not suffix type names with Type or Interface. The name should describe \nthe concept, not its implementation."
language: typescript
category: naming
rule_id: TS-TYPE-SUFFIX
priority: warn
tags:
- types
- interfaces
- antipattern
---
Do not suffix type names with Type or Interface. The name should describe 
the concept, not its implementation.

## Good

- interface Entity {}
- type Callback = () => void;

## Bad

- interface EntityInterface {} // Redundant suffix
- type CallbackType = () => void; // Redundant suffix
