---
type: Styleguide Rule
description: Indent code blocks with 2 spaces, not tabs.
language: shell
category: formatting
rule_id: TWO-SPACE-INDENT
priority: error
tags:
- formatting
- indentation
---
Indent code blocks with 2 spaces, not tabs.

## Good

- if [[ -f file ]]; then
  echo "File exists"
fi


## Bad

- if [[ -f file ]]; then
	echo "File exists"  # Tab used
fi

