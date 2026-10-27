---
type: Styleguide Rule
description: |-
  Do not export test doubles or add back doors to an API just for tests.
  Design the API so it can be tested through the real implementation's public
  API, and export a substitution interface only when there is a real need for
  substitution.
language: go
category: types
rule_id: NO-TEST-ONLY-INTERFACES
priority: info
tags:
- interfaces
- testing
- api
- google-style
---
Do not export test doubles or add back doors to an API just for tests.
Design the API so it can be tested through the real implementation's public
API, and export a substitution interface only when there is a real need for
substitution.

## Good

- // test uses the real implementation against an in-memory backend
s := store.New(memfs.New())

## Bad

- package store

type Store interface{ Get(string) ([]byte, error) }
type FakeStore struct{} // exported only for tests
func (s *store) SetTestHook(f func()) // back door
