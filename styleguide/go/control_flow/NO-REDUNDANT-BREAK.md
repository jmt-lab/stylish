---
type: Styleguide Rule
description: |-
  Do not end switch clauses with unlabeled break; Go cases do not fall
  through. Mark an intentionally empty case with a comment, and use a labeled
  break to exit an enclosing loop.
language: go
category: control_flow
rule_id: NO-REDUNDANT-BREAK
priority: warn
tags:
- switch
- break
- google-style
---
Do not end switch clauses with unlabeled break; Go cases do not fall
through. Mark an intentionally empty case with a comment, and use a labeled
break to exit an enclosing loop.

## Good

- switch x {
case "A", "B":
    buf.WriteString(x)
case "C":
    // handled outside of the switch statement
default:
    return fmt.Errorf("unknown value: %q", x)
}
- loop:
for {
    switch x {
    case "A":
        break loop // exits the loop
    }
}

## Bad

- switch x {
case "A":
    buf.WriteString(x)
    break // redundant
}
- for {
    switch x {
    case "A":
        break // only exits the switch, not the loop
    }
}
