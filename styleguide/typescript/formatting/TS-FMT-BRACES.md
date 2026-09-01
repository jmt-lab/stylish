---
type: Styleguide Rule
description: Opening brace on same line (K&R style). Prettier enforces this.
language: typescript
category: formatting
rule_id: TS-FMT-BRACES
priority: error
tags:
- braces
- style
---
Opening brace on same line (K&R style). Prettier enforces this.

## Good

- if (condition) {
  doSomething();
}

- function example() {
  return true;
}


## Bad

- if (condition)
{
  doSomething();
}

