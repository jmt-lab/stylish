---
type: Styleguide Rule
description: |-
  Capitalize and punctuate doc comments and other full-sentence comments like
  English prose. End-of-line comments, especially on struct fields, may be
  short phrases whose subject is the field.
language: go
category: comments
rule_id: COMMENT-SENTENCES
priority: warn
tags:
- comments
- grammar
- google-style
---
Capitalize and punctuate doc comments and other full-sentence comments like
English prose. End-of-line comments, especially on struct fields, may be
short phrases whose subject is the field.

## Good

- // A Server handles serving quotes from the collected works of Shakespeare.
type Server struct {
    WelcomeMessage  string // displayed when user logs in
    PageLength      int    // lines per page (optional; default: 20)
}

## Bad

- // server handles serving quotes
type Server struct{}
