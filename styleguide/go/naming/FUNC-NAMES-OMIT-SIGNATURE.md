---
type: Styleguide Rule
description: |-
  Leave parameter names, input/output types, receiver type, and pointer-ness
  out of function names unless needed to tell similar functions apart.
language: go
category: naming
rule_id: FUNC-NAMES-OMIT-SIGNATURE
priority: info
tags:
- functions
- methods
- repetition
- google-style
---
Leave parameter names, input/output types, receiver type, and pointer-ness
out of function names unless needed to tell similar functions apart.

## Good

- func (c *Config) WriteTo(w io.Writer) (int64, error)
- func Override(dest, source *Config) error
- func Transform(input *Config) *jsonconfig.Config
- func (c *Config) WriteTextTo(w io.Writer) (int64, error) // disambiguates

## Bad

- func (c *Config) WriteConfigTo(w io.Writer) (int64, error)
- func OverrideFirstWithSecond(dest, source *Config) error
- func TransformToJSON(input *Config) *jsonconfig.Config
