---
type: Styleguide Rule
description: |-
  All Go source must be formatted exactly as gofmt outputs it. Format
  generated code too (e.g. with go/format.Source).
language: go
category: formatting
rule_id: GOFMT
priority: error
tags:
- gofmt
- tooling
- google-style
---
All Go source must be formatted exactly as gofmt outputs it. Format
generated code too (e.g. with go/format.Source).

## Good

- $ gofmt -l ./... # prints nothing
- src, err := format.Source(generated)

## Bad

- func main(){
  fmt.Println("hi")} // not gofmt-formatted
