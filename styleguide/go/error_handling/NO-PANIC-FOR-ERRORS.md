---
type: Styleguide Rule
description: |-
  Do not use panic for normal error handling; return errors. Libraries should
  return errors instead of aborting, especially for transient failures. In
  main or initialization code, exit with an actionable message for fatal setup
  errors.
language: go
category: error_handling
rule_id: NO-PANIC-FOR-ERRORS
priority: error
tags:
- errors
- panic
- google-style
---
Do not use panic for normal error handling; return errors. Libraries should
return errors instead of aborting, especially for transient failures. In
main or initialization code, exit with an actionable message for fatal setup
errors.

## Good

- func Load(path string) (*Config, error) {
    data, err := os.ReadFile(path)
    if err != nil {
        return nil, fmt.Errorf("load config: %w", err)
    }
    return parse(data)
}

## Bad

- func Load(path string) *Config {
    data, err := os.ReadFile(path)
    if err != nil {
        panic(err) // library aborts the whole program
    }
    return parse(data)
}
