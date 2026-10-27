---
type: Styleguide Rule
description: |-
  Don't overuse type inference: add enough explicit types that someone
  familiar with the codebase can tell what was inferred, particularly for
  generic-return methods like .into(), .parse(), and .collect(), and for the
  results of complex iterator chains. Prefer annotating the variable over a
  turbofish; when a turbofish is required, _ is fine for the element type.
language: rust
category: functional
rule_id: ANNOTATE-INFERRED-TYPES
priority: warn
tags:
- types
- inference
- readability
- google-style
---
Don't overuse type inference: add enough explicit types that someone
familiar with the codebase can tell what was inferred, particularly for
generic-return methods like .into(), .parse(), and .collect(), and for the
results of complex iterator chains. Prefer annotating the variable over a
turbofish; when a turbofish is required, _ is fine for the element type.

## Good

- let port: u16 = env_port.parse()?;
- let by_owner: HashMap<UserId, Vec<&Repo>> = repos.iter().into_group_map_by(|r| r.owner);
- let ids = rows.iter().map(Row::id).collect::<Vec<_>>();

## Bad

- let port = env_port.parse()?; // u16? u32? usize?
- let by_owner = repos.iter().filter(..).map(..).into_group_map_by(|r| r.owner);
