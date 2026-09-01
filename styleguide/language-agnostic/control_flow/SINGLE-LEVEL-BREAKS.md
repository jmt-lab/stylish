---
type: Styleguide Rule
description: |-
  Breaking out of multiple loop levels makes control flow hard to follow.
  Use flags, restructure, or extract to functions instead. Exception:
  goto to a single cleanup label is acceptable and often clearer than
  alternatives (see GOTO-FOR-CLEANUP).
language: language-agnostic
category: control_flow
rule_id: SINGLE-LEVEL-BREAKS
priority: warn
tags:
- loops
- control-flow
- clarity
---
Breaking out of multiple loop levels makes control flow hard to follow.
Use flags, restructure, or extract to functions instead. Exception:
goto to a single cleanup label is acceptable and often clearer than
alternatives (see GOTO-FOR-CLEANUP).

## Good

- bool found = false;
for (...) {
    if (match) { found = true; break; }
}
if (found) ...
- if (error) goto cleanup; // Single cleanup label — acceptable

## Bad

- goto escape; // Breaking multiple loops with arbitrary labels
