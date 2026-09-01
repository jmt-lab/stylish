---
type: Styleguide Rule
description: Use instance methods when behavior depends on object state. Reserve static methods for pure functions or factory methods.
language: rust
category: architecture
rule_id: AVOID-STATIC-METHODS
priority: error
tags:
- architecture
- api-design
- code-organization
---
Use instance methods when behavior depends on object state. Reserve static methods for pure functions or factory methods.

## Good

- impl MyStruct { fn process(&self) -> Result<()> { /* uses self.field */ } }
- impl MyStruct { fn new() -> Self { /* factory method */ } }

## Bad

- impl MyStruct { fn process(data: &Data) -> Result<()> { /* should be instance method */ } }
