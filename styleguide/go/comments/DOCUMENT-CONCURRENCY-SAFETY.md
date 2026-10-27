---
type: Styleguide Rule
description: |-
  Readers assume read-only operations are safe for concurrent use and mutating
  ones are not, so do not restate that. Document concurrency when it is
  unclear whether an operation mutates, when the API provides synchronization,
  or when an interface requires it of implementers.
language: go
category: comments
rule_id: DOCUMENT-CONCURRENCY-SAFETY
priority: info
tags:
- documentation
- concurrency
- google-style
---
Readers assume read-only operations are safe for concurrent use and mutating
ones are not, so do not restate that. Document concurrency when it is
unclear whether an operation mutates, when the API provides synchronization,
or when an interface requires it of implementers.

## Good

- // Lookup returns the data associated with the key from the cache.
//
// This operation is not safe for concurrent use.
func (*Cache) Lookup(key string) (data []byte, ok bool) // LRU hit mutates
- // Watcher methods are safe for simultaneous use by multiple goroutines.
type Watcher interface{ Health() error }

## Bad

- // Len returns the number of unread bytes.
//
// It is safe to be called concurrently by multiple goroutines.
func (*Buffer) Len() int // already implied for read-only
