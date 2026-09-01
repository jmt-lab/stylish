---
type: Styleguide Rule
description: Prefer bash parameter expansion over external commands for simple string operations.
language: shell
category: variables
rule_id: PARAMETER-EXPANSION
priority: info
tags:
- variables
- expansion
- performance
---
Prefer bash parameter expansion over external commands for simple string operations.

## Good

- filename="${path##*/}"  # Basename
- extension="${file##*.}"  # Get extension
- name="${file%.*}"  # Remove extension
- upper="${var^^}"  # Uppercase (bash 4+)

## Bad

- filename="$(basename "${path}")"  # External command
- extension=$(echo ${file} | awk -F. '{print $NF}')  # Overkill
