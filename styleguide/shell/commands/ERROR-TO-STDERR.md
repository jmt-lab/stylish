---
type: Styleguide Rule
description: All error messages and diagnostic output must go to stderr using >&2, not stdout. Keep stdout for actual program output. This ensures errors don't pollute output that may be piped or captured.
language: shell
category: commands
rule_id: ERROR-TO-STDERR
priority: error
tags:
- error-handling
- output
- google
---
All error messages and diagnostic output must go to stderr using >&2, not stdout. Keep stdout for actual program output. This ensures errors don't pollute output that may be piped or captured.

## Good

- echo "Error: File not found" >&2

- printf 'Fatal: %s\n' "${error_msg}" >&2

- err() {
  echo "[$(date +'%Y-%m-%dT%H:%M:%S%z')]: $*" >&2
}
err "Something went wrong"


## Bad

- echo "Error: File not found"
# Goes to stdout, pollutes output

- printf 'Fatal: %s\n' "${error_msg}"
# Error on stdout

