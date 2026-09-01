---
type: Styleguide Rule
description: When you need to ensure you're calling the actual command and not an alias or function, use the 'command' builtin.
language: shell
category: commands
rule_id: USE-COMMAND-BUILTIN
priority: info
tags:
- robustness
- portability
---
When you need to ensure you're calling the actual command and not an alias or function, use the 'command' builtin.

## Good

- # Ensure we call actual ls, not alias
command ls -la

- # Bypass any rm function/alias
command rm -f "${temp_file}"


## Bad

- # Might call alias or function
ls -la

- # Could be overridden
rm -f "${temp_file}"

