---
type: Styleguide Rule
description: "Boolean functions and variables should start with is, has, can, or \nsimilar predicates to make their return type obvious."
language: language-agnostic
category: naming
rule_id: BOOL-PREDICATES
priority: info
tags:
- booleans
- functions
- clarity
---
Boolean functions and variables should start with is, has, can, or 
similar predicates to make their return type obvious.

## Good

- isValid()
- hasChildren()
- canMove()
- shouldRender

## Bad

- valid() // Ambiguous
- children() // Unclear return type
