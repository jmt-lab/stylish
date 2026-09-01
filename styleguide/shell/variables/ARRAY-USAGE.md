---
type: Styleguide Rule
description: Use bash arrays for lists instead of space-separated strings. Use [@] for all elements.
language: shell
category: variables
rule_id: ARRAY-USAGE
priority: warn
tags:
- variables
- arrays
- lists
---
Use bash arrays for lists instead of space-separated strings. Use [@] for all elements.

## Good

- files=("file1.txt" "file2.txt" "file with spaces.txt")
- for file in "${files[@]}"; do
- echo "Total: ${#files[@]} files"

## Bad

- files="file1.txt file2.txt"  # Breaks with spaces
- for file in ${files}; do  # Word splitting issues
