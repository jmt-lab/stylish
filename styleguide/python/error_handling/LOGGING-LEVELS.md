---
type: Styleguide Rule
description: |-
  Use DEBUG for diagnostics, INFO for normal events, WARNING for
  recoverable issues, ERROR for failures, CRITICAL for fatal errors.
language: python
category: error_handling
rule_id: LOGGING-LEVELS
priority: warn
tags:
- logging
- diagnostics
- severity
---
Use DEBUG for diagnostics, INFO for normal events, WARNING for
recoverable issues, ERROR for failures, CRITICAL for fatal errors.

## Good

- logger.debug(f'Processing {count} items')
- logger.warning(f'Retrying connection: {e}')
- logger.error(f'Failed to load: {path}')

## Bad

- logger.info('Critical system failure')  # Wrong level
