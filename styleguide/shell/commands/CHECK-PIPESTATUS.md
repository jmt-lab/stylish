---
type: Styleguide Rule
description: When using pipelines, check PIPESTATUS array to detect failures in any pipeline component, not just the last command.
language: shell
category: commands
rule_id: CHECK-PIPESTATUS
priority: error
tags:
- error-handling
- pipelines
- google
---
When using pipelines, check PIPESTATUS array to detect failures in any pipeline component, not just the last command.

## Good

- tar -cf - ./* | ( cd "${dir}" && tar -xf - )
if [[ "${PIPESTATUS[0]}" -ne 0 || "${PIPESTATUS[1]}" -ne 0 ]]; then
  echo "Pipeline failed" >&2
  exit 1
fi

- command1 | command2 | command3
if [[ "${PIPESTATUS[@]}" =~ [1-9] ]]; then
  echo "Pipeline component failed" >&2
  return 1
fi


## Bad

- tar -cf - ./* | ( cd "${dir}" && tar -xf - )
# Only checks last command in pipeline

- command1 | command2 | command3
if [[ $? -ne 0 ]]; then
  # Only detects command3 failure
  exit 1
fi

