---
type: Styleguide Rule
description: |-
  Empty catch blocks hide bugs. Either handle the error meaningfully or
  let it propagate. If ignoring, document why.
language: typescript
category: error_handling
rule_id: NEVER-CATCH-IGNORE
priority: error
tags:
- error-handling
- safety
- debugging
---
Empty catch blocks hide bugs. Either handle the error meaningfully or
let it propagate. If ignoring, document why.

## Good

- try { ... } catch (e) { logger.error('failed', e); throw; }
- // Explicitly ignoring: optional feature, failure is acceptable try { ... } catch { }

## Bad

- try { criticalOperation(); } catch { } // Silent failure
