---
type: Styleguide Rule
description: |-
  Go has no fixed line length. If a line feels too long, refactor it (e.g.
  extract locals) instead of wrapping. Never split before an indentation
  change or split a long string such as a URL just to fit a column.
language: go
category: formatting
rule_id: NO-FIXED-LINE-LENGTH
priority: error
tags:
- line-length
- readability
- google-style
---
Go has no fixed line length. If a line feels too long, refactor it (e.g.
extract locals) instead of wrapping. Never split before an indentation
change or split a long string such as a URL just to fit a column.

## Good

- local := helper(some, parameters, here)
good := foo.Call(list, of, parameters, local)
- const docURL = "https://example.com/a/very/long/path/that/stays/on/one/line"

## Bad

- bad := foo.Call(long, list, of, parameters,
    with, arbitrary, line, breaks) // broken only for length
- const docURL = "https://example.com/a/very/long/" +
    "path/that/was/split" // splitting a URL
