---
type: Styleguide Rule
description: Include trailing commas in comma-separated lists when followed by newlines for easier code movement and smaller diffs.
language: rust
category: formatting
rule_id: TRAILING-COMMAS
priority: warn
tags:
- formatting
- punctuation
---
Include trailing commas in comma-separated lists when followed by newlines for easier code movement and smaller diffs.

## Good

- let array = [
    element,
    another_element,
];

## Bad

- let array = [
    element,
    another_element
];
