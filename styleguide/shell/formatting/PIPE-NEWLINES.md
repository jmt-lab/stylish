---
type: Styleguide Rule
description: For pipelines, put each pipe on a new line if the command doesn't fit on one line.
language: shell
category: formatting
rule_id: PIPE-NEWLINES
priority: info
tags:
- formatting
- pipelines
---
For pipelines, put each pipe on a new line if the command doesn't fit on one line.

## Good

- command1 \
  | command2 \
  | command3


## Bad

- command1 | command2 | command3 | command4 | command5 | command6
