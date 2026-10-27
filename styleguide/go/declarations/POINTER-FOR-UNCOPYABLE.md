---
type: Styleguide Rule
description: |-
  Uncopyable fields such as sync.Mutex can be zero-value struct members, but
  then the containing type must be passed by pointer with pointer receivers.
  Declare composites that will be returned or always addressed (and proto
  messages) as pointers from the start.
language: go
category: declarations
rule_id: POINTER-FOR-UNCOPYABLE
priority: info
tags:
- structs
- sync
- pointers
- google-style
---
Uncopyable fields such as sync.Mutex can be zero-value struct members, but
then the containing type must be passed by pointer with pointer receivers.
Declare composites that will be returned or always addressed (and proto
messages) as pointers from the start.

## Good

- type Counter struct {
    mu   sync.Mutex
    data map[string]int64
}

func (c *Counter) IncrementBy(name string, n int64)
- func NewCounter(name string) *Counter {
    c := new(Counter)
    registerCounter(name, c)
    return c
}

## Bad

- func (c Counter) IncrementBy(name string, n int64) // copies the mutex
- var msg = pb.Bar{} // *pb.Bar implements proto.Message, pb.Bar does not
