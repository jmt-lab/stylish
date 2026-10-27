---
type: Styleguide Rule
description: |-
  Use an option struct as the last argument when most callers set several
  options or options are shared across functions. Fields are self-documenting,
  defaults can be omitted, and it can grow without breaking callers. Never put
  a context in it.
language: go
category: practices
rule_id: OPTION-STRUCTS
priority: info
tags:
- options
- api
- structs
- google-style
---
Use an option struct as the last argument when most callers set several
options or options are shared across functions. Fields are self-documenting,
defaults can be omitted, and it can grow without breaking callers. Never put
a context in it.

## Good

- type ReplicationOptions struct {
    Config         *replicator.Config
    PrimaryRegions []string
    CopyWorkers    int
}

storage.EnableReplication(ctx, storage.ReplicationOptions{
    Config:         config,
    PrimaryRegions: []string{"us-east1"},
})

## Bad

- type ReplicationOptions struct {
    Ctx context.Context // contexts are never option fields
    // ...
}
- storage.EnableReplication(ctx, config, nil, nil, false, true, 0, 100, nil)
