---
type: Styleguide Rule
description: |-
  Use variadic functional options when most callers need none, options are
  many or rarely used, take arguments, can fail, or may be user-defined.
  Options should take values (FailFast(bool), not EnableFailFast()), apply in
  order with the last one winning, and keep the options struct unexported.
language: go
category: practices
rule_id: VARIADIC-OPTIONS
priority: info
tags:
- options
- api
- functional-options
- google-style
---
Use variadic functional options when most callers need none, options are
many or rarely used, take arguments, can fail, or may be user-defined.
Options should take values (FailFast(bool), not EnableFailFast()), apply in
order with the last one winning, and keep the options struct unexported.

## Good

- type ReplicationOption func(*replicationOptions)

func ReplicateExisting(enabled bool) ReplicationOption {
    return func(o *replicationOptions) { o.replicateExisting = enabled }
}

storage.EnableReplication(ctx, config, cells, storage.ReplicateExisting(true))

## Bad

- func EnableReplicateExisting() ReplicationOption // presence-based; hard to set dynamically
- type ReplicationOptions struct{ ... } // exported, letting callers bypass the options
