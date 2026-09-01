---
type: Styleguide Rule
description: Prefer bash-specific constructs over external commands for better performance and portability. Avoid spawning external processes unnecessarily.
language: shell
category: commands
rule_id: PREFER-BUILTINS
priority: warn
tags:
- performance
- portability
- google
---
Prefer bash-specific constructs over external commands for better performance and portability. Avoid spawning external processes unnecessarily.

## Good

- # Use [[ ]] builtin
if [[ -f "${file}" ]]; then
  echo "File exists"
fi

- # Use parameter expansion
filename="${path##*/}"

- # Use printf builtin
printf '%s\n' "${output}"


## Bad

- # Unnecessary external command
if [ -f "${file}" ]; then
  echo "File exists"
fi

- # Spawns basename process
filename=$(basename "${path}")

- # Spawns echo when printf is better
echo -e "${output}"

