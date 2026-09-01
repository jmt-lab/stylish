---
type: Styleguide Rule
description: 'Organize scripts with: shebang, header comment, constants, functions, main logic.'
language: shell
category: organization
rule_id: SCRIPT-STRUCTURE
priority: info
tags:
- organization
- structure
---
Organize scripts with: shebang, header comment, constants, functions, main logic.

## Good

- #!/bin/bash
# Script description

set -o errexit
set -o nounset

readonly CONSTANT=value

function_one() { ... }
function_two() { ... }

main() { ... }
main "$@"


## Bad

- #!/bin/bash
# Random order of functions and logic mixed together

