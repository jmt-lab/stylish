---
type: Styleguide Rule
description: |-
  When you start a goroutine, make it obvious when and whether it exits. Keep
  the synchronization in the spawning function (WaitGroup, context, done
  channels) and document exit conditions if they are not evident. Never fire
  and forget.
language: go
category: concurrency
rule_id: GOROUTINE-LIFETIMES
priority: warn
tags:
- goroutines
- leaks
- lifecycle
- google-style
---
When you start a goroutine, make it obvious when and whether it exits. Keep
the synchronization in the spawning function (WaitGroup, context, done
channels) and document exit conditions if they are not evident. Never fire
and forget.

## Good

- func (w *Worker) Run(ctx context.Context) error {
    var wg sync.WaitGroup
    for item := range w.q {
        wg.Add(1)
        go func() {
            defer wg.Done()
            process(ctx, item) // returns when ctx is cancelled
        }()
    }
    wg.Wait() // goroutines do not outlive Run
    return nil
}

## Bad

- func (w *Worker) Run() {
    for item := range w.q {
        go process(item) // may never finish; leaks; untestable
    }
}
