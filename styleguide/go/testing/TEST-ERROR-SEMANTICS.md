---
type: Styleguide Rule
description: |-
  Do not test errors by comparing their message strings. Check presence (err
  != nil vs a wantErr bool) or semantic identity with errors.Is or
  cmpopts.EquateErrors.
language: go
category: testing
rule_id: TEST-ERROR-SEMANTICS
priority: warn
tags:
- testing
- errors
- google-style
---
Do not test errors by comparing their message strings. Check presence (err
!= nil vs a wantErr bool) or semantic identity with errors.Is or
cmpopts.EquateErrors.

## Good

- if gotErr := err != nil; gotErr != test.wantErr {
    t.Errorf("f(%q) = %v, want error presence = %v", test.input, err, test.wantErr)
}
- if !errors.Is(err, ErrNotFound) {
    t.Errorf("Get(%q) = %v, want ErrNotFound", key, err)
}

## Bad

- if err.Error() != "user not found: id 42" { // breaks on rewording
    t.Errorf(...)
}
