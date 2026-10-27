---
type: Styleguide Rule
description: |-
  If an import collides with a local variable name you want (url, ssh) and the
  package is still needed in that scope, rename it with a pkg suffix.
language: go
category: imports
rule_id: PKG-SUFFIX-FOR-SHADOWED-IMPORTS
priority: info
tags:
- imports
- shadowing
- google-style
---
If an import collides with a local variable name you want (url, ssh) and the
package is still needed in that scope, rename it with a pkg suffix.

## Good

- import urlpkg "net/url"

func fetch(url string) (*urlpkg.URL, error) { return urlpkg.Parse(url) }

## Bad

- import u "net/url" // cryptic alias
- import netURL "net/url" // mixed case alias
