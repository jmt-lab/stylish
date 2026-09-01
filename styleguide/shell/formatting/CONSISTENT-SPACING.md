---
type: Styleguide Rule
description: Use spaces around operators and after commas. No trailing whitespace.
language: shell
category: formatting
rule_id: CONSISTENT-SPACING
priority: warn
tags:
- formatting
- spacing
---
Use spaces around operators and after commas. No trailing whitespace.

## Good

- if [[ "${var}" == "value" ]]; then
- for i in 1 2 3; do

## Bad

- if [["${var}"=="value"]]; then
- for i in 1 2 3;do
