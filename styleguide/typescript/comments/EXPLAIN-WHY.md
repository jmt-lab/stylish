---
type: Styleguide Rule
description: |-
  Comments should explain reasoning, not describe what the code obviously does.
  Trust readers to understand TypeScript syntax and basic operations.
language: typescript
category: comments
rule_id: EXPLAIN-WHY
priority: warn
tags:
- content
- clarity
- intent
---
Comments should explain reasoning, not describe what the code obviously does.
Trust readers to understand TypeScript syntax and basic operations.

## Good

- // Cache result to avoid expensive recalculation on every render const memoized = useMemo(() => compute(data), [data]);
- // Workaround for Safari not supporting lookbehind regex

## Bad

- // Set count to 0 let count = 0;
- // Loop through items for (const item of items)
