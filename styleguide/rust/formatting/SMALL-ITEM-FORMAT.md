---
type: Styleguide Rule
description: Small constructs (simple, short expressions) can be formatted on a single line. Tools use heuristics based on character count and complexity.
language: rust
category: formatting
rule_id: SMALL-ITEM-FORMAT
priority: info
tags:
- formatting
- organization
---
Small constructs (simple, short expressions) can be formatted on a single line. Tools use heuristics based on character count and complexity.

## Good

- Foo { f1, f2 }
- Foo {
    f1: complex_expression(),
    f2: another_expression(),
}
