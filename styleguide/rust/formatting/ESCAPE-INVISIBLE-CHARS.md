---
type: Styleguide Rule
description: |-
  Use escape sequences for invisible or easily confused characters in
  string and char literals (zero-width joiners, non-breaking spaces, BOMs,
  etc.) so readers and reviewers can see them.
language: rust
category: formatting
rule_id: ESCAPE-INVISIBLE-CHARS
priority: warn
tags:
- formatting
- literals
- unicode
- google-style
---
Use escape sequences for invisible or easily confused characters in
string and char literals (zero-width joiners, non-breaking spaces, BOMs,
etc.) so readers and reviewers can see them.

## Good

- const ZWJ: char = '\u{200D}';
- let label = format!("{first}\u{00A0}{last}");

## Bad

- const ZWJ: char = '‍'; // looks like an empty char literal
- let label = format!("{first} {last}"); // non-breaking space is invisible
