---
type: Styleguide Rule
description: |-
  Do not repeat information supplied by the surrounding context (package,
  type, receiver, function, file) in names. Evaluate repetition from the
  caller's point of view.
language: go
category: naming
rule_id: NO-CONTEXT-REPETITION
priority: warn
tags:
- repetition
- context
- google-style
---
Do not repeat information supplied by the surrounding context (package,
type, receiver, function, file) in names. Evaluate repetition from the
caller's point of view.

## Good

- // In package "sqldb"
type Connection struct{}
- func (p *Project) Name() string
- func (db *DB) UserCount() (int, error) {
    var count int64
    if err := db.Load("count(distinct users)", &count); err != nil {
        return 0, err
    }
    return int(count), nil
}

## Bad

- // In package "sqldb"
type DBConnection struct{}
- func (p *Project) ProjectName() string
- func (db *DB) UserCount() (userCount int, err error) {
    var userCountInt64 int64
    if dbLoadError := db.LoadFromDatabase(q, &userCountInt64); dbLoadError != nil { ... }
}
