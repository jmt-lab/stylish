---
type: Styleguide Rule
description: |-
  Treat acronyms as one word: Uuid, HttpClient, and JsonValue in
  UpperCamelCase; is_xid_start and http_client in snake_case.
language: rust
category: naming
rule_id: ACRONYMS-AS-WORDS
priority: warn
tags:
- naming
- acronyms
- official
- beautiful-rust
---
Treat acronyms as one word: Uuid, HttpClient, and JsonValue in
UpperCamelCase; is_xid_start and http_client in snake_case.

## Good

- pub struct HttpClient;
- pub struct Uuid([u8; 16]);
- fn parse_json(input: &str)

## Bad

- pub struct HTTPClient;
- pub struct UUID([u8; 16]);
- fn parse_JSON(input: &str)
