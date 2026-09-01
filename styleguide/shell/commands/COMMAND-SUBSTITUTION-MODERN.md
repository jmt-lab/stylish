---
type: Styleguide Rule
description: Use $(command) syntax instead of backticks for command substitution. It's more readable, nests properly, and always quote the result to prevent word splitting.
language: shell
category: commands
rule_id: COMMAND-SUBSTITUTION-MODERN
priority: warn
tags:
- readability
- google
- variables
- substitution
- commands
---
Use $(command) syntax instead of backticks for command substitution. It's more readable, nests properly, and always quote the result to prevent word splitting.

## Good

- current_dir="$(pwd)"

- # For multi-line results, use mapfile
mapfile -t files < <(find . -name "*.sh")

- # Nesting works cleanly
outer="$(echo "inner=$(date)")"

- result="$(command arg)"  # Quoted result

## Bad

- current_dir=`pwd`

- files=`find . -name "*.sh"`

- # Nesting requires escaping
outer=`echo "inner=\`date\`"`

- result=$(command arg)  # Unquoted, word splitting
