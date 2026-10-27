---
type: Styleguide Rule
description: |-
  Don't put design journals, "why we picked X over Y" essays, change
  histories, or rule-compliance tables in code docs. Document the end state:
  what the item does and what callers must know. Enduring architecture notes
  belong in a README or design doc.
language: rust
category: documentation
rule_id: NO-META-DESIGN-DOCS
priority: warn
tags:
- documentation
- comments
- ai
- beautiful-rust
---
Don't put design journals, "why we picked X over Y" essays, change
histories, or rule-compliance tables in code docs. Document the end state:
what the item does and what callers must know. Enduring architecture notes
belong in a README or design doc.

## Good

- /// Caches resolved DNS entries for their TTL.

## Bad

- /// ## Design notes
/// Originally used a Vec, then switched to HashMap per review feedback.
/// | Rule | Applied | Where |
/// | NO-UNWRAP | yes | line 40 |
