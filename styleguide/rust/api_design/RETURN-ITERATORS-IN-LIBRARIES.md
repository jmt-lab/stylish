---
type: Styleguide Rule
description: |-
  Reusable library code should prefer returning iterators (a concrete type
  or impl Iterator) over Vec<T>, letting callers choose whether to collect,
  loop, or chain further. Return Vec when most callers need one anyway, the
  implementation naturally builds one, random access is expected, the
  function's purpose is building a collection, or it returns an existing vec.
  Application code may return Vec when it is simpler.
language: rust
category: api_design
rule_id: RETURN-ITERATORS-IN-LIBRARIES
priority: info
tags:
- api-design
- iterators
- libraries
- google-style
---
Reusable library code should prefer returning iterators (a concrete type
or impl Iterator) over Vec<T>, letting callers choose whether to collect,
loop, or chain further. Return Vec when most callers need one anyway, the
implementation naturally builds one, random access is expected, the
function's purpose is building a collection, or it returns an existing vec.
Application code may return Vec when it is simpler.

## Good

- pub fn active_users(&self) -> impl Iterator<Item = &User> + '_ {
    self.users.iter().filter(|user| user.is_active())
}

## Bad

- pub fn active_users(&self) -> Vec<&User> {
    self.users.iter().filter(|user| user.is_active()).collect()
} // forces an allocation even for callers that only need .count()
