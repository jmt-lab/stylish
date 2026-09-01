---
type: Styleguide Rule
description: Create clear abstraction boundaries around domain concepts for separation of concerns and modularity. Domain defines trait interfaces, infrastructure implements traits with concrete details, domain never depends on infrastructure implementation.
language: rust
category: architecture
rule_id: ABSTRACTION-BOUNDARIES
priority: warn
tags:
- architecture
- abstraction
- modules
- api-design
---
Create clear abstraction boundaries around domain concepts for separation of concerns and modularity. Domain defines trait interfaces, infrastructure implements traits with concrete details, domain never depends on infrastructure implementation.

## Good

- trait UserRepository {
    fn find_by_id(&self, id: UserId) -> Result<User>;
}
struct PostgresUserRepository { /* impl details */ }
impl UserRepository for PostgresUserRepository { /* ... */ }


## Bad

- struct UserService {
    db_pool: PgPool,  // domain depends on infrastructure
}

