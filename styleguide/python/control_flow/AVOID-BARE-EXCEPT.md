---
type: Styleguide Rule
description: |-
  Bare except catches everything including KeyboardInterrupt and
  SystemExit. Always catch and raise specific exception types. This makes
  error handling explicit and prevents hiding unexpected failures. Use the
  most specific exception type possible (e.g., FileNotFoundError over
  Exception).
language: python
category: control_flow
rule_id: AVOID-BARE-EXCEPT
priority: error
tags:
- exceptions
- error-handling
- safety
- specificity
- correctness
---
Bare except catches everything including KeyboardInterrupt and
SystemExit. Always catch and raise specific exception types. This makes
error handling explicit and prevents hiding unexpected failures. Use the
most specific exception type possible (e.g., FileNotFoundError over
Exception).

## Good

- try:
    risky()
except ValueError:
    handle()
- try:
    risky()
except Exception as e:
    log(e)
- try:
    data = load_file(path)
except FileNotFoundError:
    handle_missing_file()
- raise ValueError(f'Invalid size: {size}')

## Bad

- try:
    risky()
except:
    pass  # Catches everything!
- try:
    data = load_file(path)
except:
    pass  # Hides all errors
- except Exception:  # Too broad
