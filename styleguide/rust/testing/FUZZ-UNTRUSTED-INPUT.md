---
type: Styleguide Rule
description: |-
  Fuzz parsers and decoders of untrusted input with cargo fuzz, and keep
  the corpus and any crash reproducers as regression tests.
language: rust
category: testing
rule_id: FUZZ-UNTRUSTED-INPUT
priority: info
tags:
- testing
- fuzzing
- security
- beautiful-rust
---
Fuzz parsers and decoders of untrusted input with cargo fuzz, and keep
the corpus and any crash reproducers as regression tests.

## Good

- // fuzz/fuzz_targets/parse_packet.rs
fuzz_target!(|data: &[u8]| { let _ = Packet::parse(data); });

## Bad

- // network packet parser tested only with three hand-written inputs
