---
type: Styleguide Rule
description: Enum variants should use UpperCamelCase.
language: rust
category: naming
rule_id: UPPER-CAMEL-ENUM-VARIANTS
priority: error
tags:
- naming
- convention
- official
---
Enum variants should use UpperCamelCase.

## Good

- enum Status { Success, Failure, Pending }
- enum RenderPass { Shadow, Opaque, Transparent }

## Bad

- enum Status { success, failure }
