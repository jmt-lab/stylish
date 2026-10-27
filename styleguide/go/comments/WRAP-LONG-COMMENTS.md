---
type: Styleguide Rule
description: |-
  Wrap long comment paragraphs (80-100 columns is common) so source reads well
  in tools that do not soft-wrap. There is no hard limit; do not break long
  URLs or literal text, and be consistent within a file.
language: go
category: comments
rule_id: WRAP-LONG-COMMENTS
priority: info
tags:
- comments
- line-length
- google-style
---
Wrap long comment paragraphs (80-100 columns is common) so source reads well
in tools that do not soft-wrap. There is no hard limit; do not break long
URLs or literal text, and be consistent within a file.

## Good

- // This is a comment paragraph.
// The choice of wrapping makes it easy to read on narrow screens.
//
// https://example.com/a/very/long/url/that/stays/on/one/line/Animalia/Chordata/

## Bad

- // This is a comment paragraph that crams several sentences onto one enormous line that overflows most windows and forces readers to scroll horizontally to finish reading it.
