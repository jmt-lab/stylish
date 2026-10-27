---
type: Styleguide Rule
description: |-
  Make failures diagnosable without reading the test: name the function, show
  the (short) inputs, and print got before want in the form YourFunc(%v) = %v,
  want %v. Use the words got and want.
language: go
category: testing
rule_id: FAILURE-MESSAGE-FORMAT
priority: warn
tags:
- testing
- failure-messages
- google-style
---
Make failures diagnosable without reading the test: name the function, show
the (short) inputs, and print got before want in the form YourFunc(%v) = %v,
want %v. Use the words got and want.

## Good

- t.Errorf("Compare(%q, %q) = %v, want %v", a, b, got, want)

## Bad

- t.Errorf("got %v, want %v", got, want) // which function? which input?
- t.Errorf("expected %v but was %v", want, got) // want-first, non-standard words
- t.Error("test failed")
