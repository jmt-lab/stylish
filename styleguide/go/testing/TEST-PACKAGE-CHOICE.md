---
type: Styleguide Rule
description: |-
  Put tests in package foo (in foo_test.go) to reach unexported identifiers,
  or in package foo_test for black-box tests, integration tests without a home
  package, and to break import cycles.
language: go
category: testing
rule_id: TEST-PACKAGE-CHOICE
priority: info
tags:
- testing
- packages
- google-style
---
Put tests in package foo (in foo_test.go) to reach unexported identifiers,
or in package foo_test for black-box tests, integration tests without a home
package, and to break import cycles.

## Good

- // foo_test.go
package foo
- // integration test
package gmailintegration_test

## Bad

- package foo_test_utils // invalid _test package naming
- // package foo test importing "path/to/foo" from within package foo
