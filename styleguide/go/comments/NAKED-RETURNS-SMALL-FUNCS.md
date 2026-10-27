---
type: Styleguide Rule
description: |-
  Use naked returns only in small functions; in anything medium-sized return
  values explicitly. Naming a result is always fine when a deferred closure
  must modify it.
language: go
category: comments
rule_id: NAKED-RETURNS-SMALL-FUNCS
priority: warn
tags:
- functions
- results
- clarity
- google-style
---
Use naked returns only in small functions; in anything medium-sized return
values explicitly. Naming a result is always fine when a deferred closure
must modify it.

## Good

- func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return
}
- func (s *Store) Save() (err error) {
    defer func() { err = errors.Join(err, s.close()) }()
    return s.write()
}

## Bad

- func process(in []byte) (out []byte, n int, err error) {
    // ...40 lines...
    return // what is returned here?
}
