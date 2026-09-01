---
type: Styleguide Rule
description: |-
  Distinguish between warning (recoverable), error (serious), and fatal
  (unrecoverable). Make severity explicit in types and logging.
language: typescript
category: error_handling
rule_id: ERROR-SEVERITY
priority: warn
tags:
- logging
- severity
- diagnostics
---
Distinguish between warning (recoverable), error (serious), and fatal
(unrecoverable). Make severity explicit in types and logging.

## Good

- type Severity = 'warning' | 'error' | 'fatal';
- logger.warn('missing optional field');
- logger.error('failed to load critical resource');
- logger.fatal('out of memory'); process.exit(1);

## Bad

- console.log('something went wrong'); // Unclear severity
