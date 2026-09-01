---
type: Styleguide Rule
description: Enable pipefail to make pipelines return the exit status of the first failing command, not just the last. Without it, only the last command's exit status is checked and earlier failures are silently ignored.
language: shell
category: features
rule_id: PIPEFAIL-FOR-PIPES
priority: warn
tags:
- error-handling
- pipelines
- safety
- robustness
---
Enable pipefail to make pipelines return the exit status of the first failing command, not just the last. Without it, only the last command's exit status is checked and earlier failures are silently ignored.

## Good

- set -o pipefail
if ! command1 | command2 | command3; then
  echo "Pipeline failed" >&2
  exit 1
fi

- #!/bin/bash
set -euo pipefail

# Now any pipeline failure will exit
data=$(curl -s "${url}" | jq '.field')


## Bad

- # No pipefail set
command1 | command2 | command3
# command1 failure is ignored

- # Without pipefail, only command3 failure detected
if ! command1 | command2 | command3; then
  exit 1
fi

