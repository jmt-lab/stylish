---
type: Styleguide Rule
description: |-
  Avoid package names likely to be shadowed by common local variable names,
  and avoid naming locals after standard packages outside tiny scopes, since
  that hides the package.
language: go
category: naming
rule_id: PACKAGE-NAME-NOT-SHADOWED
priority: warn
tags:
- packages
- shadowing
- google-style
---
Avoid package names likely to be shadowed by common local variable names,
and avoid naming locals after standard packages outside tiny scopes, since
that hides the package.

## Good

- package usercount
- func fetch() { u := "https://example.com/"; parsed, _ := url.Parse(u) }

## Bad

- package count // clients will want a local named count
- func LongFunction() {
    url := "https://example.com/"
    // net/url is now inaccessible below
}
