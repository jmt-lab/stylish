---
type: Styleguide Rule
description: "Generic type parameters should be descriptive (TEntity, TKey) rather than \nsingle letters, except for simple cases like T for single generic."
language: typescript
category: naming
rule_id: TS-GENERIC-SINGLE
priority: info
tags:
- generics
- clarity
---
Generic type parameters should be descriptive (TEntity, TKey) rather than 
single letters, except for simple cases like T for single generic.

## Good

- function map<T>(items: T[]): T[] // Simple case
- class Cache<TKey, TValue> {} // Multiple generics
- interface Repository<TEntity> {} // Descriptive

## Bad

- class Cache<K, V> {} // Single letters for complex
- interface Repository<A> {} // Unclear meaning
