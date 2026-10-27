---
type: Styleguide Rule
description: |-
  If you return an error, do not also log it; let the caller decide whether to
  log, rate-limit, recover, or exit. Make log messages actionable and
  diagnostic, keep PII out of logs, and reserve ERROR level for actionable
  problems.
language: go
category: error_handling
rule_id: RETURN-OR-LOG-NOT-BOTH
priority: info
tags:
- errors
- logging
- google-style
---
If you return an error, do not also log it; let the caller decide whether to
log, rate-limit, recover, or exit. Make log messages actionable and
diagnostic, keep PII out of logs, and reserve ERROR level for actionable
problems.

## Good

- if err != nil {
    return fmt.Errorf("fetch user %d: %w", id, err)
}

## Bad

- if err != nil {
    log.Errorf("fetch user failed: %v", err) // logged here...
    return err // ...and again by every caller
}
- log.Infof("login failed for %s with password %s", email, pw) // PII
