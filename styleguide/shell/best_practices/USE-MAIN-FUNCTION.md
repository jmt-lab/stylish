---
type: Styleguide Rule
description: Put script logic in a main() function and call it at the end.
language: shell
category: best_practices
rule_id: USE-MAIN-FUNCTION
priority: info
tags:
- organization
- structure
---
Put script logic in a main() function and call it at the end.

## Good

- main() {
  # Script logic here
}

main "$@"


## Bad

- # Script logic at top level
echo "Starting..."

