---
type: Styleguide Rule
description: 'Use #!/bin/bash for consistency. Avoid #!/bin/sh (may not be bash) and #!/usr/bin/env bash (less predictable).'
language: shell
category: best_practices
rule_id: USE-BASH-SHEBANG
priority: error
tags:
- shebang
- portability
---
Use #!/bin/bash for consistency. Avoid #!/bin/sh (may not be bash) and #!/usr/bin/env bash (less predictable).

## Good

- #!/bin/bash

## Bad

- #!/bin/sh
- #!/usr/bin/env bash  # Avoid for consistency
