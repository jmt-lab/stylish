---
type: Styleguide Rule
description: Use // for comments instead of /* ... */.
language: rust
category: comments
rule_id: LINE-COMMENTS
priority: warn
tags:
- comments
- style
- official
---
Use // for comments instead of /* ... */.

## Good

- // This is a comment
- // Multi-line comments
// use multiple line comments

## Bad

- /* This is a comment */
