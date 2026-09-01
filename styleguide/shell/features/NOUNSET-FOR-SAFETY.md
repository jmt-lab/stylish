---
type: Styleguide Rule
description: Use set -o nounset (set -u) to catch undefined variable references. Requires careful handling of optional parameters using ${var:-default} or ${var+x} patterns. Catches typos and uninitialized variables that would otherwise silently expand to empty strings.
language: shell
category: features
rule_id: NOUNSET-FOR-SAFETY
priority: warn
tags:
- safety
- error-detection
- variables
- validation
---
Use set -o nounset (set -u) to catch undefined variable references. Requires careful handling of optional parameters using ${var:-default} or ${var+x} patterns. Catches typos and uninitialized variables that would otherwise silently expand to empty strings.

## Good

- set -o nounset
# Use parameter expansion for optional vars
value="${optional_var:-default}"

- set -u  # Error on unset variables
- name="${name:-default}"  # Provide default
- if [[ -n "${var+x}" ]]; then  # Check if set

## Bad

- # No nounset, typos go unnoticed
echo "${optinal_var}"

- echo "${undefined_var}"  # Silent empty string
- rm -rf /${prefix}data  # Catastrophic if prefix unset
