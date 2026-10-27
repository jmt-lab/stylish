---
type: Styleguide Rule
description: |-
  Receiver names must be short (one or two letters), an abbreviation of the
  type, consistent across all methods of the type, and never this, self, or _.
  Omit the name if it is unused.
language: go
category: naming
rule_id: RECEIVER-NAMES
priority: warn
tags:
- receivers
- methods
- google-style
---
Receiver names must be short (one or two letters), an abbreviation of the
type, consistent across all methods of the type, and never this, self, or _.
Omit the name if it is unused.

## Good

- func (t Tray) Size() int
- func (ri *ResearchInfo) Summary() string
- func (w *ReportWriter) Flush() error
- func (*Scanner) Name() string // unused receiver omitted

## Bad

- func (tray Tray) Size() int // too long
- func (this *ReportWriter) Flush() error
- func (self *Scanner) Scan() bool
- func (_ *Scanner) Name() string
