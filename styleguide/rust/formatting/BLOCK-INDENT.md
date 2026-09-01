---
type: Styleguide Rule
description: Use block indentation rather than visual indentation for smaller diffs and less rightward drift.
language: rust
category: formatting
rule_id: BLOCK-INDENT
priority: warn
tags:
- formatting
- indentation
---
Use block indentation rather than visual indentation for smaller diffs and less rightward drift.

## Good

- a_function_call(
    foo,
    bar,
);

## Bad

- a_function_call(foo,
                bar);
