---
type: Styleguide Rule
description: |-
  Use the map entry API for insert-or-update instead of a contains_key or
  get check followed by insert, which hashes the key twice and invites
  logic slips.
language: rust
category: collections
rule_id: ENTRY-API
priority: warn
tags:
- collections
- maps
- idioms
- performance
- rust-skills
---
Use the map entry API for insert-or-update instead of a contains_key or
get check followed by insert, which hashes the key twice and invites
logic slips.

## Good

- *word_counts.entry(word).or_insert(0) += 1;

sessions.entry(user_id).or_insert_with(Session::new).touch();

## Bad

- if word_counts.contains_key(&word) {
    *word_counts.get_mut(&word).unwrap() += 1;
} else {
    word_counts.insert(word, 1);
}
