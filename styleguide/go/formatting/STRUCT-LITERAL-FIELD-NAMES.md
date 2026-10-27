---
type: Styleguide Rule
description: |-
  Always use field names in struct literals for types from other packages;
  positional fields couple you to field order and the full field set. Field
  names are optional for package-local types but preferred for structs with
  many fields.
language: go
category: formatting
rule_id: STRUCT-LITERAL-FIELD-NAMES
priority: warn
tags:
- literals
- structs
- coupling
- google-style
---
Always use field names in struct literals for types from other packages;
positional fields couple you to field order and the full field set. Field
names are optional for package-local types but preferred for structs with
many fields.

## Good

- r := csv.Reader{
    Comma:           ',',
    Comment:         '#',
    FieldsPerRecord: 4,
}
- p := point{3, 4} // small package-local type

## Bad

- r := csv.Reader{',', '#', 4, false, false, false, false}
