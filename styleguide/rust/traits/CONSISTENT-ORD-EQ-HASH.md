---
type: Styleguide Rule
description: |-
  If you hand-write Ord, PartialEq, or Hash, hand-write all of them so they
  compare and hash the same fields. A derived PartialEq beside a custom Ord, or
  a Hash that disagrees with Eq, silently corrupts BTreeMap, HashMap, sort,
  and dedup. Document which fields equality ignores.
language: rust
category: traits
rule_id: CONSISTENT-ORD-EQ-HASH
priority: error
tags:
- traits
- ord
- eq
- hash
- correctness
- beautiful-rust
---
If you hand-write Ord, PartialEq, or Hash, hand-write all of them so they
compare and hash the same fields. A derived PartialEq beside a custom Ord, or
a Hash that disagrees with Eq, silently corrupts BTreeMap, HashMap, sort,
and dedup. Document which fields equality ignores.

## Good

- /// Equality, hashing, and ordering ignore `build` metadata.
impl PartialEq for Version { fn eq(&self, o: &Self) -> bool { self.key() == o.key() } }
impl Eq for Version {}
impl Hash for Version { fn hash<H: Hasher>(&self, h: &mut H) { self.key().hash(h) } }
impl Ord for Version { fn cmp(&self, o: &Self) -> Ordering { self.key().cmp(&o.key()) } }
impl PartialOrd for Version { fn partial_cmp(&self, o: &Self) -> Option<Ordering> { Some(self.cmp(o)) } }

## Bad

- #[derive(PartialEq, Eq, Hash)]
pub struct Version { major: u64, minor: u64, build: String }

impl Ord for Version { ... } // ignores build; derived Eq compares it
