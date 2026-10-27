---
type: Styleguide Rule
description: |-
  Do not restate that cancelling ctx interrupts a function and returns
  ctx.Err(); that is implied. Document only non-standard context behavior: a
  different error on cancel, other interruption mechanisms, or requirements on
  deadline, lineage, or values.
language: go
category: comments
rule_id: DOCUMENT-CONTEXT-EXCEPTIONS
priority: info
tags:
- documentation
- context
- google-style
---
Do not restate that cancelling ctx interrupts a function and returns
ctx.Err(); that is implied. Document only non-standard context behavior: a
different error on cancel, other interruption mechanisms, or requirements on
deadline, lineage, or values.

## Good

- // Run executes the worker's run loop.
func (Worker) Run(ctx context.Context) error
- // Run executes the worker's run loop.
//
// If the context is cancelled, Run returns a nil error.
func (Worker) Run(ctx context.Context) error

## Bad

- // Run executes the worker's run loop.
//
// The method processes work until the context is cancelled and then
// returns an error.
func (Worker) Run(ctx context.Context) error
