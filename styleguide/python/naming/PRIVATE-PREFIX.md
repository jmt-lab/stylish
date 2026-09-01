---
type: Styleguide Rule
description: |-
  Use single leading underscore for internal functions, methods, and
  variables not intended as public API.
language: python
category: naming
rule_id: PRIVATE-PREFIX
priority: warn
tags:
- encapsulation
- privacy
- pep8
---
Use single leading underscore for internal functions, methods, and
variables not intended as public API.

## Good

- def _internal_helper():
- self._cache = {}
- _module_constant = 42

## Bad

- def internalHelper(): # No prefix
- self.cache = {} # Public-looking internal state
