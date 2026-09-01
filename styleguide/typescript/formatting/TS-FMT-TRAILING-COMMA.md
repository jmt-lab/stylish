---
type: Styleguide Rule
description: Use trailing commas in multiline arrays, objects, function parameters.
language: typescript
category: formatting
rule_id: TS-FMT-TRAILING-COMMA
priority: info
tags:
- commas
- git-diff
---
Use trailing commas in multiline arrays, objects, function parameters.

## Good

- const obj = {
  a: 1,
  b: 2,
};

- function example(
  arg1: string,
  arg2: number,
) {}


## Bad

- const obj = {
  a: 1,
  b: 2
};

