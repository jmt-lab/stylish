---
type: Styleguide Rule
description: |-
  Keep implementation details private, expose only domain-focused interfaces
  to improve maintainability and reduce coupling. Make struct fields private
  by default — use pub only when external access is required. Provide
  getter/setter methods for controlled access to maintain invariants. Hide
  database, HTTP client, and serialization details behind abstractions.
  Return domain types, not raw database or API responses.
language: rust
category: architecture
rule_id: PRIVATE-IMPLEMENTATION
priority: error
tags:
- architecture
- abstraction
- api-design
- safety
---
Keep implementation details private, expose only domain-focused interfaces
to improve maintainability and reduce coupling. Make struct fields private
by default — use pub only when external access is required. Provide
getter/setter methods for controlled access to maintain invariants. Hide
database, HTTP client, and serialization details behind abstractions.
Return domain types, not raw database or API responses.

## Good

- pub struct Cache {
    pool: Pool,  // private
}
impl Cache {
    pub fn get(&self, key: &str) -> Option<Value> { /* ... */ }
}

- struct User { name: String, email: String } impl User { pub fn name(&self) -> &str { &self.name } }
- pub fn get_user(&self, id: UserId) -> Result<User>

## Bad

- pub struct Cache {
    pub pool: Pool,  // exposed implementation
}

- struct User { pub name: String, pub email: String }
- pub fn get_user(&self, id: UserId) -> Result<sqlx::Row>
- pub fn fetch(&self) -> Result<reqwest::Response>
