---
type: Styleguide Rule
description: |-
  Write sans-IO code where possible: functions that consume or produce a
  byte stream take impl Read / impl Write (or AsyncRead/AsyncWrite) rather
  than opening files or sockets themselves. Generic R: Read and W: Write are
  taken by value; callers pass &mut r to keep using it.
language: rust
category: api_design
rule_id: ACCEPT-READ-WRITE
priority: info
tags:
- api-design
- io
- testability
- beautiful-rust
---
Write sans-IO code where possible: functions that consume or produce a
byte stream take impl Read / impl Write (or AsyncRead/AsyncWrite) rather
than opening files or sockets themselves. Generic R: Read and W: Write are
taken by value; callers pass &mut r to keep using it.

## Good

- pub fn parse_log<R: BufRead>(reader: R) -> Result<Summary, ParseError> { ... }

## Bad

- pub fn parse_log(path: &str) -> Result<Summary, ParseError> { ... } // can't test without a file
