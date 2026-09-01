---
type: Styleguide Rule
description: Check return values of commands using $?, if statements, or || operators. Never ignore command failures silently.
language: shell
category: commands
rule_id: CHECK-RETURN-VALUES
priority: error
tags:
- error-handling
- robustness
- google
---
Check return values of commands using $?, if statements, or || operators. Never ignore command failures silently.

## Good

- if ! mv "${file_list[@]}" "${dest_dir}/"; then
  echo "Unable to move files" >&2
  exit 1
fi

- command_that_might_fail || {
  echo "Command failed" >&2
  return 1
}

- if grep -q "pattern" file.txt; then
  echo "Pattern found"
fi


## Bad

- mv "${file_list[@]}" "${dest_dir}/"
# No check - failure ignored

- grep "pattern" file.txt
# Return value ignored

