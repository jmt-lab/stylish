---
type: Styleguide Rule
description: |-
  When code looks like a common idiom but differs subtly, such as err == nil
  instead of err != nil, add a short comment so the difference is not missed.
language: go
category: comments
rule_id: SIGNAL-BOOST-UNUSUAL-CODE
priority: info
tags:
- comments
- readability
- google-style
---
When code looks like a common idiom but differs subtly, such as err == nil
instead of err != nil, add a short comment so the difference is not missed.

## Good

- if err := doSomething(); err == nil { // if NO error
    // ...
}

## Bad

- if err := doSomething(); err == nil {
    // easily misread as the usual err != nil check
}
