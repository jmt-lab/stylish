---
type: Styleguide Rule
description: |-
  Document every cleanup the caller is responsible for (Stop, Close, cancel),
  and show how when it is not obvious, so callers do not leak resources.
language: go
category: comments
rule_id: DOCUMENT-CLEANUP
priority: warn
tags:
- documentation
- resources
- google-style
---
Document every cleanup the caller is responsible for (Stop, Close, cancel),
and show how when it is not obvious, so callers do not leak resources.

## Good

- // NewTicker returns a new Ticker.
//
// Call Stop to release the Ticker's associated resources when done.
func NewTicker(d Duration) *Ticker
- // When err is nil, resp always contains a non-nil resp.Body.
// Caller should close resp.Body when done reading from it.
func (c *Client) Get(url string) (resp *Response, err error)

## Bad

- // NewTicker returns a new Ticker.
func NewTicker(d Duration) *Ticker // Stop requirement undocumented
