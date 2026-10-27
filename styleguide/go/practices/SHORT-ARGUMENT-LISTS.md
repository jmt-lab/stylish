---
type: Styleguide Rule
description: |-
  Do not let function signatures grow long; many parameters, especially
  adjacent ones of the same type, are easy to confuse. Split highly
  configurable functions, or use an option struct or variadic options, judged
  by how call sites read.
language: go
category: practices
rule_id: SHORT-ARGUMENT-LISTS
priority: info
tags:
- functions
- api
- parameters
- google-style
---
Do not let function signatures grow long; many parameters, especially
adjacent ones of the same type, are easy to confuse. Split highly
configurable functions, or use an option struct or variadic options, judged
by how call sites read.

## Good

- func EnableReplication(ctx context.Context, opts ReplicationOptions)

## Bad

- func EnableReplication(ctx context.Context, config *replicator.Config, primaryRegions, readonlyRegions []string, replicateExisting, overwritePolicies bool, replicationInterval time.Duration, copyWorkers int, healthWatcher health.Watcher)
