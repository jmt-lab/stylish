---
type: Styleguide Rule
description: |-
  Name command-line flags in snake_case and the Go variables holding them in
  the equivalent mixedCaps. Group global flag variables in their own var block
  after the imports.
language: go
category: practices
rule_id: FLAG-NAMING
priority: warn
tags:
- flags
- naming
- cli
- google-style
---
Name command-line flags in snake_case and the Go variables holding them in
the equivalent mixedCaps. Group global flag variables in their own var block
after the imports.

## Good

- var (
    pollInterval = flag.Duration("poll_interval", time.Minute, "Interval to use for polling.")
)

## Bad

- var (
    poll_interval = flag.Int("pollIntervalSeconds", 60, "Interval in seconds.")
)
