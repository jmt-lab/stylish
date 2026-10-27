---
type: Styleguide Rule
description: |-
  Create root contexts with context.Background() only at entrypoints (main,
  init) and in server frameworks. Library and mid-call-chain code should take
  the caller's context, and tests should use t.Context().
language: go
category: concurrency
rule_id: CONTEXT-BACKGROUND-AT-ENTRYPOINTS
priority: warn
tags:
- context
- libraries
- google-style
---
Create root contexts with context.Background() only at entrypoints (main,
init) and in server frameworks. Library and mid-call-chain code should take
the caller's context, and tests should use t.Context().

## Good

- func main() {
    ctx := context.Background()
    if err := app.Run(ctx); err != nil { log.Fatal(err) }
}
- func TestRun(t *testing.T) { err := Run(t.Context()) }

## Bad

- func (s *Store) Save(rec Record) error {
    ctx := context.Background() // ignores caller cancellation and deadlines
    return s.db.Exec(ctx, rec)
}
