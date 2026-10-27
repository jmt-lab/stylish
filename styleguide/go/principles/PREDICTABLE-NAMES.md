---
type: Styleguide Rule
description: |-
  Use the same name for the same concept across parameters, receivers, and
  functions in a package so readers can predict names and refactoring stays
  easy.
language: go
category: principles
rule_id: PREDICTABLE-NAMES
priority: info
tags:
- maintainability
- naming
- consistency
- google-style
---
Use the same name for the same concept across parameters, receivers, and
functions in a package so readers can predict names and refactoring stays
easy.

## Good

- func (s *Store) Get(ctx context.Context, key string) ([]byte, error)
func (s *Store) Put(ctx context.Context, key string, val []byte) error

## Bad

- func (s *Store) Get(c context.Context, k string) ([]byte, error)
func (st *Store) Put(ctx context.Context, keyName string, val []byte) error
