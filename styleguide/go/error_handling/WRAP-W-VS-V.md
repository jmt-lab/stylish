---
type: Styleguide Rule
description: |-
  Wrap with %w when callers should inspect the underlying error via
  errors.Is/As and that is part of your contract. Use %v for human-readable
  annotation or at system boundaries (RPC, storage), where you translate
  errors into a canonical space instead of leaking internals.
language: go
category: error_handling
rule_id: WRAP-W-VS-V
priority: info
tags:
- errors
- wrapping
- google-style
---
Wrap with %w when callers should inspect the underlying error via
errors.Is/As and that is part of your contract. Use %v for human-readable
annotation or at system boundaries (RPC, storage), where you translate
errors into a canonical space instead of leaking internals.

## Good

- // internal helper: callers may check errors.Is(err, fs.ErrNotExist)
return fmt.Errorf("couldn't find remote file: %w", err)
- // RPC boundary: hide internal details
return nil, status.Errorf(codes.Internal, "couldn't find fortune database: %v", err)

## Bad

- // RPC handler leaking a wrapped filesystem error to clients
return nil, fmt.Errorf("db: %w", err)
