---
type: Styleguide Rule
description: |-
  Don't use abbreviations, acronyms, or initialisms that someone outside
  your project is unlikely to know, and don't abbreviate by deleting letters
  within a word. Widely known abbreviations (e.g. those common enough to
  appear on Wikipedia, like IpAddr or Http) are fine.
language: rust
category: naming
rule_id: AVOID-ABBREVIATIONS
priority: warn
tags:
- naming
- readability
- abbreviations
- google-style
---
Don't use abbreviations, acronyms, or initialisms that someone outside
your project is unlikely to know, and don't abbreviate by deleting letters
within a word. Widely known abbreviations (e.g. those common enough to
appear on Wikipedia, like IpAddr or Http) are fine.

## Good

- let retry_count = 3;
- struct IpAddr { ... }
- fn connection_timeout() -> Duration { ... }

## Bad

- let rtry_cnt = 3;
- struct UsrMgr { ... }
- fn cnxn_tmo() -> Duration { ... }
