---
type: Styleguide Rule
description: Use 'set -o errexit' (or 'set -e') to exit on command failures.
language: shell
category: best_practices
rule_id: SET-ERREXIT
priority: error
tags:
- error-handling
- safety
---
Use 'set -o errexit' (or 'set -e') to exit on command failures.

## Good

- #!/bin/bash
set -o errexit
set -o nounset
set -o pipefail


## Bad

- #!/bin/bash
# No error handling

