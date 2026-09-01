---
type: Styleguide Rule
description: |-
  Use explicit scope delimiters (braces) even for single-line blocks
  when it improves clarity or prevents future bugs.
language: language-agnostic
category: organization
rule_id: EXPLICIT-SCOPE
priority: info
tags:
- scope
- safety
- clarity
---
Use explicit scope delimiters (braces) even for single-line blocks
when it improves clarity or prevents future bugs.

## Good

- if (condition) {
    DoSomething();
}

## Bad

- if (condition)
    DoSomething();
    DoSomethingElse(); // Bug waiting to happen
