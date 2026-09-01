---
type: Styleguide Rule
description: Prefer single quotes for strings. Use double quotes for JSX attributes.
language: typescript
category: formatting
rule_id: TS-FMT-QUOTES
priority: info
tags:
- quotes
- strings
---
Prefer single quotes for strings. Use double quotes for JSX attributes.

## Good

- const message = 'hello';
- const jsx = <div className="box" />;

## Bad

- const message = "hello";
