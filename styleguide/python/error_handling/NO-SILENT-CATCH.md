---
type: Styleguide Rule
description: |-
  Don't catch exceptions without handling them. If you must ignore,
  document why explicitly.
language: python
category: error_handling
rule_id: NO-SILENT-CATCH
priority: error
tags:
- exceptions
- correctness
- debugging
---
Don't catch exceptions without handling them. If you must ignore,
document why explicitly.

## Good

- try:
    cleanup()
except OSError as e:
    logger.warning(f'Cleanup failed: {e}')
- try:
    optional_feature()
except ImportError:
    pass  # Feature optional, documented in design

## Bad

- try:
    important_operation()
except Exception:
    pass  # Hiding errors
