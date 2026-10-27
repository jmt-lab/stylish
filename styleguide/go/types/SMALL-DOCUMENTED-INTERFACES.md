---
type: Styleguide Rule
description: |-
  Keep interfaces small and compose larger ones from them. Document the
  contract, edge cases, and expected errors: on the type for single-method
  interfaces and on each method otherwise, including unexported interfaces.
language: go
category: types
rule_id: SMALL-DOCUMENTED-INTERFACES
priority: info
tags:
- interfaces
- documentation
- google-style
---
Keep interfaces small and compose larger ones from them. Document the
contract, edge cases, and expected errors: on the type for single-method
interfaces and on each method otherwise, including unexported interfaces.

## Good

- // A Watcher reports the health of some entity.
type Watcher interface {
    // Health returns nil if the entity is healthy, or an error explaining why not.
    Health() error
}
- type ReadWriter interface {
    Reader
    Writer
}

## Bad

- type Manager interface { // many undocumented methods
    Start(); Stop(); Reload(); Health() error; Stats() map[string]int
}
