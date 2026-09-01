---
type: Styleguide Rule
description: Check if required external commands exist before attempting to use them, especially for optional dependencies. Use 'command -v' or 'type -P' to verify availability and provide clear error messages when missing.
language: shell
category: commands
rule_id: TEST-COMMAND-EXISTS
priority: warn
tags:
- robustness
- portability
- dependencies
- error-handling
---
Check if required external commands exist before attempting to use them, especially for optional dependencies. Use 'command -v' or 'type -P' to verify availability and provide clear error messages when missing.

## Good

- if ! command -v jq >/dev/null 2>&1; then
  echo "Error: jq is required but not installed" >&2
  exit 1
fi

- if type -P docker >/dev/null; then
  docker run "${image}"
else
  echo "Docker not found, skipping" >&2
fi

- if ! command -v jq &> /dev/null; then
  echo "Error: jq is required" >&2
  exit 1
fi


## Bad

- # Assumes jq exists
jq '.field' < file.json

- # No check for docker
docker run "${image}"

- # Just use jq without checking
jq '.field' file.json

