---
type: Styleguide Rule
description: |-
  Propagate initialization errors (bad flags, config) up to main, which exits
  with a human-readable, actionable message rather than a stack trace.
language: go
category: error_handling
rule_id: INIT-ERRORS-TO-MAIN
priority: info
tags:
- errors
- initialization
- main
- google-style
---
Propagate initialization errors (bad flags, config) up to main, which exits
with a human-readable, actionable message rather than a stack trace.

## Good

- func main() {
    flag.Parse()
    cfg, err := loadConfig(*configPath)
    if err != nil {
        log.Exitf("Invalid --config %q: %v; see docs/config.md", *configPath, err)
    }
    run(cfg)
}

## Bad

- func loadConfig(path string) *Config {
    if path == "" {
        log.Fatal("no config") // deep in library code, stack trace not helpful
    }
}
