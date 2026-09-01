---
type: Styleguide Rule
description: |-
  Use double leading underscore only to avoid name conflicts in subclasses.
  Rarely needed; prefer single underscore for most internal use.
language: python
category: naming
rule_id: NAME-MANGLING
priority: info
tags:
- encapsulation
- classes
---
Use double leading underscore only to avoid name conflicts in subclasses.
Rarely needed; prefer single underscore for most internal use.

## Good

- self.__private_field = value # Avoid subclass collision

## Bad

- self.__helper() # Unnecessary mangling
