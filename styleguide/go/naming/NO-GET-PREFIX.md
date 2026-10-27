---
type: Styleguide Rule
description: |-
  Do not prefix getters with Get; start with the noun (Counts, not GetCounts).
  Use Get only when the concept itself is "get" (HTTP GET), and prefer Compute
  or Fetch for expensive or remote operations.
language: go
category: naming
rule_id: NO-GET-PREFIX
priority: warn
tags:
- getters
- functions
- google-style
---
Do not prefix getters with Get; start with the noun (Counts, not GetCounts).
Use Get only when the concept itself is "get" (HTTP GET), and prefer Compute
or Fetch for expensive or remote operations.

## Good

- func (c *Config) JobName(key string) (value string, ok bool)
- func (c *Client) FetchUser(ctx context.Context, id string) (*User, error) // remote call

## Bad

- func (c *Config) GetJobName(key string) (value string, ok bool)
- func (s *Stats) GetCounts() []int
