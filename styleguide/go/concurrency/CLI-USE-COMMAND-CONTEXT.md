---
type: Styleguide Rule
description: |-
  In CLI frameworks, use the context the framework supplies (cobra's
  cmd.Context(), subcommands' ctx parameter) instead of creating a new root
  context in each command.
language: go
category: concurrency
rule_id: CLI-USE-COMMAND-CONTEXT
priority: info
tags:
- cli
- context
- google-style
---
In CLI frameworks, use the context the framework supplies (cobra's
cmd.Context(), subcommands' ctx parameter) instead of creating a new root
context in each command.

## Good

- RunE: func(cmd *cobra.Command, args []string) error {
    return run(cmd.Context(), args)
}

## Bad

- RunE: func(cmd *cobra.Command, args []string) error {
    return run(context.Background(), args)
}
