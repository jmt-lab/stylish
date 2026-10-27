---
type: Styleguide Rule
description: |-
  Create an interface only when there is a real need: several implementations
  handled by the same logic, decoupling packages, or narrowing a huge API. Do
  not add interfaces for named patterns like Service or Repository, or wrap
  RPC clients just for testing.
language: go
category: types
rule_id: INTERFACES-WHEN-NEEDED
priority: warn
tags:
- interfaces
- abstraction
- google-style
---
Create an interface only when there is a real need: several implementations
handled by the same logic, decoupling packages, or narrowing a huge API. Do
not add interfaces for named patterns like Service or Repository, or wrap
RPC clients just for testing.

## Good

- type UserStore struct{ db *sql.DB } // concrete until a second implementation appears
- // consumer needs only one method of a large client
type blobReader interface {
    ReadBlob(ctx context.Context, key string) ([]byte, error)
}

## Bad

- type UserService interface { // single implementation, "because it is a service"
    Get(id string) (*User, error)
}
type userService struct{}
- type FooClient interface { Call(...) } // wraps a generated RPC client just for mocks
