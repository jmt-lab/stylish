---
type: Styleguide Rule
description: Prefer [[ ]] over [ ] or test command. It is less error-prone with quoting, supports additional operators like =~ for regex matching, and is safer and more powerful for conditionals.
language: shell
category: features
rule_id: DOUBLE-BRACKET-TESTS
priority: warn
tags:
- syntax
- safety
- testing
- conditionals
---
Prefer [[ ]] over [ ] or test command. It is less error-prone with quoting, supports additional operators like =~ for regex matching, and is safer and more powerful for conditionals.

## Good

- if [[ -f "${file}" ]]; then
- if [[ "${var}" == "value" ]]; then
- if [[ "${str}" =~ ^[0-9]+$ ]]; then

## Bad

- if [ -f "${file}" ]; then
- if test -f "${file}"; then
- if [ "${var}" == "value" ]; then
