---
type: Styleguide Rule
description: |-
  When code handles browser quirks or platform differences, document
  which browsers/versions are affected and why the workaround is needed.
language: typescript
category: comments
rule_id: BROWSER-PLATFORM-NOTES
priority: warn
tags:
- platform
- browser
- compatibility
---
When code handles browser quirks or platform differences, document
which browsers/versions are affected and why the workaround is needed.

## Good

- // Safari < 15 doesn't support structuredClone const clone = typeof structuredClone === 'function' ? structuredClone(obj) : JSON.parse(JSON.stringify(obj));
- // Node.js-specific: use process.hrtime for high-resolution timing

## Bad

- // Browser check if (isSafari)
