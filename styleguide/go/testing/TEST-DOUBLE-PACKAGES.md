---
type: Styleguide Rule
description: |-
  Put test doubles in a package named after the production package plus test
  (creditcardtest). Name doubles concisely (Stub) when there is one type, by
  behavior (AlwaysCharges, AlwaysDeclines) for variants, and by type
  (StubService) when several types need doubles.
language: go
category: testing
rule_id: TEST-DOUBLE-PACKAGES
priority: info
tags:
- testing
- test-doubles
- naming
- google-style
---
Put test doubles in a package named after the production package plus test
(creditcardtest). Name doubles concisely (Stub) when there is one type, by
behavior (AlwaysCharges, AlwaysDeclines) for variants, and by type
(StubService) when several types need doubles.

## Good

- package creditcardtest

// Stub stubs creditcard.Service and provides no behavior of its own.
type Stub struct{}
- type AlwaysDeclines struct{}

## Bad

- package creditcardmocks
type StubCreditCardService struct{} // repeats package context
