---
type: Styleguide Rule
description: |-
  Write exactly one package comment per package, directly above the package
  clause with no blank line, starting "Package name ...". For main packages,
  name the binary instead. Long package docs may go in doc.go.
language: go
category: comments
rule_id: PACKAGE-COMMENT
priority: warn
tags:
- documentation
- packages
- godoc
- google-style
---
Write exactly one package comment per package, directly above the package
clause with no blank line, starting "Package name ...". For main packages,
name the binary instead. Long package docs may go in doc.go.

## Good

- // Package math provides basic constants and mathematical functions.
//
// This package does not guarantee bit-identical results across architectures.
package math
- // The seed_generator command generates a seed file from JSON configs.
package main

## Bad

- // Provides math helpers.

package math // blank line detaches the comment; wrong opening
- // Package math ... (repeated in several files of the same package)
