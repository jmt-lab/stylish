---
type: Styleguide Rule
description: |-
  Name constants with MixedCaps after the role they play, not their value. Do
  not use SCREAMING_CASE or a k prefix; a constant with no role beyond its
  value is unnecessary.
language: go
category: naming
rule_id: CONSTANT-NAMES-BY-ROLE
priority: warn
tags:
- constants
- mixedcaps
- google-style
---
Name constants with MixedCaps after the role they play, not their value. Do
not use SCREAMING_CASE or a k prefix; a constant with no role beyond its
value is unnecessary.

## Good

- const MaxPacketSize = 512
- const (
    ExecuteBit = 1 << iota
    WriteBit
    ReadBit
)

## Bad

- const MAX_PACKET_SIZE = 512
- const kMaxBufferSize = 1024
- const Twelve = 12 // named after its value
