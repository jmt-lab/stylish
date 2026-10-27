---
type: Styleguide Rule
description: |-
  Give every top-level exported name a doc comment, plus unexported types and
  functions whose behavior is not obvious. Begin with the name being described
  (optionally preceded by a, an, or the) and write full sentences.
language: go
category: comments
rule_id: DOC-COMMENT-EXPORTED-NAMES
priority: warn
tags:
- documentation
- godoc
- exports
- google-style
---
Give every top-level exported name a doc comment, plus unexported types and
functions whose behavior is not obvious. Begin with the name being described
(optionally preceded by a, an, or the) and write full sentences.

## Good

- // A Request represents a request to run a command.
type Request struct{}
- // Encode writes the JSON encoding of req to w.
func Encode(w io.Writer, req *Request) error
- // parseRetryHeader parses Retry-After, accepting seconds or an HTTP date.
func parseRetryHeader(v string) time.Duration

## Bad

- type Request struct{} // exported, undocumented
- // This function writes JSON.
func Encode(w io.Writer, req *Request) error // does not start with the name
