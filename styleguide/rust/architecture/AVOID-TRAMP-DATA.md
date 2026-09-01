---
type: Styleguide Rule
description: Use dependency injection instead of passing data through layers that don't use it. Create context objects to bundle related parameters.
language: rust
category: architecture
rule_id: AVOID-TRAMP-DATA
priority: warn
tags:
- architecture
- dependencies
- code-organization
---
Use dependency injection instead of passing data through layers that don't use it. Create context objects to bundle related parameters.

## Good

- struct Context { config: Config, logger: Logger } fn process(&self, ctx: &Context)

## Bad

- fn a(config: Config) { b(config) } fn b(config: Config) { c(config) } fn c(config: Config) { /* uses config */ }
