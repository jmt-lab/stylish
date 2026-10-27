---
type: Styleguide Rule
description: |-
  Link to other items in doc comments with intra-doc links ([`Type`],
  [`Self::method`]) rather than bare names or hard-coded URLs, and keep
  rustdoc::broken_intra_doc_links clean.
language: rust
category: documentation
rule_id: INTRA-DOC-LINKS
priority: info
tags:
- documentation
- rustdoc
- links
- beautiful-rust
---
Link to other items in doc comments with intra-doc links ([`Type`],
[`Self::method`]) rather than bare names or hard-coded URLs, and keep
rustdoc::broken_intra_doc_links clean.

## Good

- /// Returns a [`Session`]. Call [`Session::close`] to release it.

## Bad

- /// Returns a Session. Call close() (see https://docs.rs/mycrate/0.3.1/mycrate/struct.Session.html).
