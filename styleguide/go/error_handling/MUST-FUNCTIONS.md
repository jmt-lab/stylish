---
type: Styleguide Rule
description: |-
  Name helpers that stop the program on failure MustXYZ, and call them only at
  startup or package initialization with constant inputs (or in tests, where
  they call t.Fatal). Never use them where ordinary error handling is
  possible.
language: go
category: error_handling
rule_id: MUST-FUNCTIONS
priority: warn
tags:
- errors
- panic
- initialization
- google-style
---
Name helpers that stop the program on failure MustXYZ, and call them only at
startup or package initialization with constant inputs (or in tests, where
they call t.Fatal). Never use them where ordinary error handling is
possible.

## Good

- func MustParse(version string) *Version {
    v, err := Parse(version)
    if err != nil {
        panic(fmt.Sprintf("MustParse(%q) = _, %v", version, err))
    }
    return v
}

var DefaultVersion = MustParse("1.2.3")

## Bad

- func Version(o *pb.Object) (*version.Version, error) {
    v := version.MustParse(o.GetVersionString()) // user input; return an error
    return dealias(v)
}
