---
type: Styleguide Rule
description: |-
  Distinguish between warning (recoverable), error (serious), and fatal
  error (unrecoverable). Make severity explicit in logging.
language: language-agnostic
category: error_handling
rule_id: ERROR-SEVERITY-LEVELS
priority: warn
tags:
- logging
- severity
- diagnostics
---
Distinguish between warning (recoverable), error (serious), and fatal
error (unrecoverable). Make severity explicit in logging.

## Good

- Warning('Missing optional config');
- Error('Failed to load critical asset');
- FatalError('Out of memory');

## Bad

- Log('Something went wrong'); // Unclear severity
