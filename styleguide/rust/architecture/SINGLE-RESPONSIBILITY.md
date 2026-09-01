---
type: Styleguide Rule
description: Each struct should have one clear purpose. Decompose god objects. Use composition to combine focused components.
language: rust
category: architecture
rule_id: SINGLE-RESPONSIBILITY
priority: error
tags:
- architecture
- code-organization
- maintainability
---
Each struct should have one clear purpose. Decompose god objects. Use composition to combine focused components.

## Good

- struct UserValidator { rules: Vec<Rule> } struct UserRepository { db: Database }

## Bad

- struct UserManager { db: Database, validator: Validator, emailer: Emailer, logger: Logger }
