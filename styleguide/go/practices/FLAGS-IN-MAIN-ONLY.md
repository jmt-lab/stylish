---
type: Styleguide Rule
description: |-
  Define flags only in package main. Configure libraries through Go APIs
  (parameters, option structs, fields), so importing a library never adds
  flags as a side effect.
language: go
category: practices
rule_id: FLAGS-IN-MAIN-ONLY
priority: warn
tags:
- flags
- libraries
- configuration
- google-style
---
Define flags only in package main. Configure libraries through Go APIs
(parameters, option structs, fields), so importing a library never adds
flags as a side effect.

## Good

- // package main
var cacheSize = flag.Int("cache_size", 128, "Entries to cache.")
store := cache.New(cache.Options{Size: *cacheSize})

## Bad

- // package cache (library)
var size = flag.Int("cache_size", 128, "Entries to cache.") // leaks into every binary
