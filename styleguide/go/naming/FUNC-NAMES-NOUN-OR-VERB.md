---
type: Styleguide Rule
description: |-
  Give functions that return something noun-like names and functions that do
  something verb-like names. When variants differ only by type, append the
  type, omitting it from a clear primary version.
language: go
category: naming
rule_id: FUNC-NAMES-NOUN-OR-VERB
priority: info
tags:
- functions
- methods
- google-style
---
Give functions that return something noun-like names and functions that do
something verb-like names. When variants differ only by type, append the
type, omitting it from a clear primary version.

## Good

- func (c *Config) JobName(key string) (string, bool)
- func (c *Config) WriteDetail(w io.Writer) (int64, error)
- func ParseInt(s string) (int, error)
func ParseInt64(s string) (int64, error)
- func (c *Config) Marshal() ([]byte, error)
func (c *Config) MarshalText() (string, error)

## Bad

- func (c *Config) GetJobName(key string) (string, bool)
- func (c *Config) Detail(w io.Writer) (int64, error) // performs an action, needs a verb
- func IntParse(s string) (int, error)
