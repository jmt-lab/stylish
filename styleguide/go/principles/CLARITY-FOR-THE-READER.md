---
type: Styleguide Rule
description: |-
  Write for the reader, not the writer. Make what the code does obvious
  through naming, structure, and whitespace, and explain why in comments when
  there are language or business nuances. Do not add comments that restate the
  code.
language: go
category: principles
rule_id: CLARITY-FOR-THE-READER
priority: warn
tags:
- clarity
- readability
- google-style
---
Write for the reader, not the writer. Make what the code does obvious
through naming, structure, and whitespace, and explain why in comments when
there are language or business nuances. Do not add comments that restate the
code.

## Good

- // Impersonating admins must still pass the real user's ACL check.
if !acl.Allowed(realUser, resource) {
    return errDenied
}

## Bad

- // increment i
i++
- if !acl.Allowed(u2, r) { return e } // opaque names, no rationale for u2
