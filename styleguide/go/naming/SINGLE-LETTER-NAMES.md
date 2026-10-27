---
type: Styleguide Rule
description: |-
  Use single-letter names only where the full word is obvious and repeating it
  would be noisy: receivers, loop indices and coordinates, and conventional
  names like r for io.Reader or *http.Request and w for io.Writer or
  http.ResponseWriter.
language: go
category: naming
rule_id: SINGLE-LETTER-NAMES
priority: info
tags:
- variables
- readability
- google-style
---
Use single-letter names only where the full word is obvious and repeating it
would be noisy: receivers, loop indices and coordinates, and conventional
names like r for io.Reader or *http.Request and w for io.Writer or
http.ResponseWriter.

## Good

- func handle(w http.ResponseWriter, r *http.Request)
- for i := 0; i < n; i++ {}
- for x, y := 0, 0; x < width; x, y = x+1, y+1 {}

## Bad

- func process(q *Queue, m map[string]int, z bool) // opaque in a long body
- for _, e := range employees { /* 40 lines using e */ }
