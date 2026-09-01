---
type: Styleguide Rule
description: |-
  If switch cases intentionally fall through, document with explicit
  comment. This distinguishes intentional from accidental.
language: language-agnostic
category: control_flow
rule_id: SWITCH-FALLTHROUGH-COMMENT
priority: warn
tags:
- switch
- fallthrough
- clarity
---
If switch cases intentionally fall through, document with explicit
comment. This distinguishes intentional from accidental.

## Good

- case A:
    DoA();
    // Fallthrough
case B:
    DoB();

## Bad

- case A:
    DoA();
case B: // Accidental or intentional?
