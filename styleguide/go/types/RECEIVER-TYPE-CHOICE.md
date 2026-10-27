---
type: Styleguide Rule
description: |-
  Choose receiver type for correctness first. Use pointers to mutate, for
  uncopyable fields (sync.Mutex), large structs, or fields pointing at mutable
  data. Use values for maps, funcs, channels, unmodified slices, built-ins,
  and small immutable structs. When in doubt use a pointer, and keep all
  methods of a type the same kind.
language: go
category: types
rule_id: RECEIVER-TYPE-CHOICE
priority: warn
tags:
- receivers
- methods
- pointers
- google-style
---
Choose receiver type for correctness first. Use pointers to mutate, for
uncopyable fields (sync.Mutex), large structs, or fields pointing at mutable
data. Use values for maps, funcs, channels, unmodified slices, built-ins,
and small immutable structs. When in doubt use a pointer, and keep all
methods of a type the same kind.

## Good

- type Counter struct {
    mu    sync.Mutex
    total int
}
func (c *Counter) Inc() { c.mu.Lock(); defer c.mu.Unlock(); c.total++ }
- type Header map[string][]string
func (h Header) Add(key, value string)
- func (t Time) Add(d Duration) Time

## Bad

- func (c Counter) Inc() { c.total++ } // mutation lost; mutex copied
- func (h *Header) Add(key, value string) // needless pointer to map
- func (c *Config) Name() string
func (c Config) Port() int // mixed receiver kinds
