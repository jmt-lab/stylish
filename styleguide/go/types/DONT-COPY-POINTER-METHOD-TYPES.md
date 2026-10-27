---
type: Styleguide Rule
description: |-
  Do not copy values of a type whose methods use pointer receivers (*T), such
  as bytes.Buffer or sync.Mutex; copies can alias internal state. Structs that
  hold such fields should be taken and returned as pointers.
language: go
category: types
rule_id: DONT-COPY-POINTER-METHOD-TYPES
priority: warn
tags:
- copying
- aliasing
- sync
- google-style
---
Do not copy values of a type whose methods use pointer receivers (*T), such
as bytes.Buffer or sync.Mutex; copies can alias internal state. Structs that
hold such fields should be taken and returned as pointers.

## Good

- type Record struct {
    buf bytes.Buffer
}

func New() *Record
func (r *Record) Process()
func Consumer(r *Record)

## Bad

- b1 := bytes.Buffer{}
b2 := b1 // b2 may alias b1's internal array
- func (r Record) Process() // copies r.buf
- func Consumer(r Record) // copies r.buf
