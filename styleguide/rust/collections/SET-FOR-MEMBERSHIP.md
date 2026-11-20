---
type: Styleguide Rule
description: |-
  Use a HashSet or BTreeSet for repeated membership tests and
  deduplication instead of Vec::contains in a loop, which is quadratic.
language: rust
category: collections
rule_id: SET-FOR-MEMBERSHIP
priority: warn
tags:
- collections
- sets
- performance
- rust-skills
---
Use a HashSet or BTreeSet for repeated membership tests and
deduplication instead of Vec::contains in a loop, which is quadratic.

## Good

- let banned: HashSet<&str> = banned_users.iter().map(String::as_str).collect();
let allowed: Vec<_> = users.iter().filter(|user| !banned.contains(user.name.as_str())).collect();

## Bad

- let allowed: Vec<_> = users
    .iter()
    .filter(|user| !banned_users.contains(&user.name)) // O(n * m)
    .collect();
