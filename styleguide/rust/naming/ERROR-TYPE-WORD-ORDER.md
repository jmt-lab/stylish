---
type: Styleguide Rule
description: |-
  Name error types verb-object-error, matching std (ParseIntError,
  FromUtf8Error).
language: rust
category: naming
rule_id: ERROR-TYPE-WORD-ORDER
priority: info
tags:
- naming
- errors
- official
- beautiful-rust
---
Name error types verb-object-error, matching std (ParseIntError,
FromUtf8Error).

## Good

- pub struct ParseConfigError { ... }
- pub struct ConnectPeerError { ... }

## Bad

- pub struct ConfigParseError { ... }
- pub struct PeerConnectionErr { ... }
