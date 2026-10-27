---
type: Styleguide Rule
description: |-
  Specify channel direction (<-chan, chan<-) in parameters and fields wherever
  possible. The compiler then catches misuse, and the type documents
  ownership.
language: go
category: declarations
rule_id: CHANNEL-DIRECTION
priority: info
tags:
- channels
- concurrency
- types
- google-style
---
Specify channel direction (<-chan, chan<-) in parameters and fields wherever
possible. The compiler then catches misuse, and the type documents
ownership.

## Good

- func sum(values <-chan int) int
- func produce(out chan<- int)

## Bad

- func sum(values chan int) (out int) {
    for v := range values {
        out += v
    }
    close(values) // receiver closing: panics on double close
}
