---
type: Styleguide Rule
description: Every script should start with a comment describing its purpose, usage, and any important notes.
language: shell
category: comments
rule_id: FILE-HEADER
priority: warn
tags:
- comments
- documentation
---
Every script should start with a comment describing its purpose, usage, and any important notes.

## Good

- #!/bin/bash
#
# Script to process log files and generate reports.
# Usage: process_logs.sh <input_dir> <output_file>
#


## Bad

- #!/bin/bash
# Just some script

