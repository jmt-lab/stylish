---
type: Styleguide Rule
description: |-
  If switch cases intentionally fall through, add explicit comment.
  Distinguishes intentional from accidental.
language: typescript
category: control_flow
rule_id: TS-NO-FALLTHROUGH
priority: warn
tags:
- switch
- fallthrough
- clarity
---
If switch cases intentionally fall through, add explicit comment.
Distinguishes intentional from accidental.

## Good

- case 'a':
  doA();
  // fallthrough
case 'b':
  doB();
  break;

## Bad

- case 'a':
  doA();
case 'b': // Accidental?
