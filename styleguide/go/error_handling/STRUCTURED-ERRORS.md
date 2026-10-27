---
type: Styleguide Rule
description: |-
  If callers need to tell error conditions apart, give errors structure
  (sentinel values, typed errors) and check them with == or
  errors.Is/errors.As. Never match on the error string.
language: go
category: error_handling
rule_id: STRUCTURED-ERRORS
priority: info
tags:
- errors
- sentinels
- errors-is
- google-style
---
If callers need to tell error conditions apart, give errors structure
(sentinel values, typed errors) and check them with == or
errors.Is/errors.As. Never match on the error string.

## Good

- var ErrDuplicate = errors.New("duplicate")

switch err := process(an); {
case errors.Is(err, ErrDuplicate):
    return fmt.Errorf("feed %q: %v", an, err)
}
- var pathErr *fs.PathError
if errors.As(err, &pathErr) { retry(pathErr.Path) }

## Bad

- if strings.Contains(err.Error(), "duplicate") { ... }
- if regexp.MustCompile(`marsupial`).MatchString(err.Error()) { ... }
