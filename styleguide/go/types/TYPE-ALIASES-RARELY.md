---
type: Styleguide Rule
description: |-
  Use a type definition (type T1 T2) to create a new type. Use a type alias
  (type T1 = T2) only for rare cases such as migrating a type to a new
  package.
language: go
category: types
rule_id: TYPE-ALIASES-RARELY
priority: info
tags:
- aliases
- types
- google-style
---
Use a type definition (type T1 T2) to create a new type. Use a type alias
(type T1 = T2) only for rare cases such as migrating a type to a new
package.

## Good

- type Celsius float64
- // Deprecated: moved to newpkg.Widget.
type Widget = newpkg.Widget

## Bad

- type UserID = string // alias where a distinct type was intended
