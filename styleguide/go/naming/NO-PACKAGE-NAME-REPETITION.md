---
type: Styleguide Rule
description: |-
  Do not repeat the package name in exported symbols; callers always see it.
  If a package exports one main type named after the package, call its
  constructor New.
language: go
category: naming
rule_id: NO-PACKAGE-NAME-REPETITION
priority: warn
tags:
- repetition
- packages
- exports
- google-style
---
Do not repeat the package name in exported symbols; callers always see it.
If a package exports one main type named after the package, call its
constructor New.

## Good

- widget.New()
- widget.NewWithName(name)
- db.Load(query)
- yamlconfig.Parse(input)

## Bad

- widget.NewWidget()
- db.LoadFromDatabase(query)
- yamlconfig.ParseYAMLConfig(input)
