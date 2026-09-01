---
type: Styleguide Rule
description: Group related parameters into dedicated struct types. Use builder pattern for objects with many optional fields.
language: rust
category: architecture
rule_id: EXTRACT-PARAM-OBJECTS
priority: warn
tags:
- architecture
- api-design
- code-organization
---
Group related parameters into dedicated struct types. Use builder pattern for objects with many optional fields.

## Good

- struct ConnectionConfig { host: String, port: u16, timeout: Duration } fn connect(config: ConnectionConfig)

## Bad

- fn connect(host: String, port: u16, timeout: Duration, retry: bool, tls: bool)
