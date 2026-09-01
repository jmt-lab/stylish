---
type: Styleguide Rule
description: Inline comments should explain reasoning, not restate obvious code. Python is readable; trust the reader to understand syntax.
language: python
category: comments
rule_id: EXPLAIN-WHY-NOT-WHAT
priority: warn
tags:
- inline-comments
- clarity
- intent
---
Inline comments should explain reasoning, not restate obvious code. Python is readable; trust the reader to understand syntax.

## Good

- # Cache result to avoid expensive recalculation in tight loop
cached_value = compute_heavy_operation()
- # Workaround for Python 3.8 bug in asyncio.run()
loop.run_until_complete(coro)

## Bad

- # Set x to 5
x = 5
- # Loop through items
for item in items:
