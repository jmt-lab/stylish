---
type: Skill
name: rust-review
description: >-
  Review Rust code against the stylish Rust styleguide and report prioritized, rule-cited
  findings that each have a concrete failure scenario and fix. Use this whenever the user
  asks to review, audit, critique, or check Rust code, a .rs file, a diff, or a PR, or asks
  whether code is idiomatic, sound, safe, or production-ready, including targeted asks
  like "is this unsafe block sound?" or "is my error handling right?". Pairs with
  rust-best-practices (writing) and rust-async (Tokio services).
---

# Rust review

A review finds the defects that matter and grounds each one in a rule. It doesn't restyle
code the tools already police, and it doesn't relitigate house rules. Rule IDs appear in
`CAPS-WITH-DASHES` and live in `styleguide/rust/<category>/<RULE-ID>.md`. Use the argosy
`search_rules` tool to find the rules that match the code in front of you.

## 1. Establish context first

- Read `Cargo.toml`: the edition, `rust-version`, whether this is a library or a binary,
  and the key dependencies (tokio, serde, tracing, bevy, a `-sys` crate). Library code is
  held to the `api_design` and `traits` rules. Application code is held to simplicity.
- Scope the review to what was asked: the diff, the named files, or the named concern. If
  the user asks about one concern ("is this unsafe sound?"), answer that concern first and
  list others only if they are severe.
- If you can run them, run `cargo clippy --all-targets --all-features -- -D warnings` and
  `cargo test`. Report what they find as one summarized item rather than restating each
  lint as a finding.

## 2. Pick the rules the code triggers

| Code contains | Read these categories and rules first |
|---|---|
| `unsafe`, raw pointers, `extern`, `transmute` | `safety/*`, UNSAFE-JUSTIFICATION, DOCUMENT-UNSAFE-CONTRACTS |
| `async`, `.await`, `tokio`, `select!`, channels | `concurrency/*`, and the `rust-async` checklist |
| `Mutex`, atomics, threads, `static` | `concurrency/*`, NO-STATIC-MUT, AVOID-GLOBAL-MUTABLE-STATE |
| `Result`, `?`, `unwrap`, `expect`, error enums | `error_handling/*` (SNAFU house rules) |
| `pub` items in a library | `api_design/*`, `traits/*`, `naming/*`, `documentation/*` |
| `#[derive(Serialize, Deserialize)]` | `serde/*`, SERDE-BEHIND-FEATURE |
| `tracing`, `log`, `println!` | `observability/*`, LOG-NOT-PRINT |
| Arithmetic on external input, floats, `as` casts | `numeric/*`, FROM-OVER-AS-CASTS |
| Loops over maps, sets, and vectors | `collections/*`, `functional/*`, `memory/*` |
| `macro_rules!`, `proc_macro` | `macros/*` |
| `Cargo.toml`, `build.rs`, features | `cargo/*`, `practices/*` |
| `#[test]`, benches | `testing/*` |
| `bevy` dependency | `bevy/*` and `skill/rust-best-practices/references/bevy.md` |

## 3. Review in severity order

Go through the code in this order, and spend most of the effort near the top.

1. **Soundness.** Undefined behavior, unsound safe APIs, missing SAFETY justifications,
   `static mut`, `mem::zeroed` on invalid types, panics unwinding across FFI. A rule with
   `priority: error` that applies here is P0 or P1.
2. **Correctness.** Silently discarded errors (NEVER-SILENTLY-DISCARD-ERRORS), overflow on
   external input, float equality, blocking or lock-across-await in async code,
   non-cancel-safe `select!`, detached tasks, missing timeouts, output that depends on
   `HashMap` order, and `unwrap` on input that can fail.
3. **Security and operability.** Secrets in logs or `Debug`, unvalidated input,
   deserialization that bypasses invariants, and unbounded channels or buffers.
4. **API and design.** Library API rules, invalid states that can be represented,
   stringly typed parameters, leaked dependency types, missing std traits.
5. **Idioms and performance.** Clones that only satisfy the borrow checker, `&String` and
   `&Vec` parameters, needless allocation, map and loop idioms. Raise performance only
   where it is measurable or the path is obviously hot (PROFILE-FIRST).
6. **Docs and tests.** Missing docs on public items, examples that `unwrap`, no test for
   a bug fix, tautological tests.

Skip formatting; rustfmt owns it.

## 4. Verify before you report

- Confirm each finding against the actual code, not a pattern match. Ask what input or
  interleaving triggers it. If you can't describe one, it isn't a finding.
- Check that the cited rule applies: whether the code is library or application, whether
  the edition is 2024, and whether a `#[expect(..., reason = ...)]` already justifies the
  exception.
- House rules win over outside advice. Don't suggest anyhow or thiserror, `# Errors`
  sections, or single-letter type parameters.
- Collapse repeats. One finding per root cause, listing the other locations.

## 5. Report

Lead with a one-line verdict, then the findings, most severe first:

```text
Verdict: 1 P0, 2 P1, 3 P2. Not ready to merge: the unsafe block in ring.rs is unsound.

[P0] src/ring.rs:88-94 (MAYBEUNINIT-FOR-UNINIT-MEMORY)
  `mem::zeroed::<Slot>()` creates a zeroed `Box` inside `Slot`, which is UB the moment it
  exists. Any call to `RingBuffer::new` triggers it.
  Fix: store `[MaybeUninit<Slot>; N]` and track the initialized range.

[P1] src/worker.rs:41 (NEVER-SILENTLY-DISCARD-ERRORS)
  `let _ = ack_tx.send(receipt);` drops the error when the client disconnects, so the job
  is marked done but never acknowledged. ...
```

- Priorities: **P0** is UB, data loss, or a security hole. **P1** is a bug users will hit.
  **P2** violates a `warn` rule with a real cost. **P3** is an `info`-level improvement.
  Keep P3s to the few that matter most.
- Each finding gives the location, the rule ID, what is wrong, a concrete failure
  scenario, and a fix, as a code snippet when one is short.
- End with what is good about the code, briefly, if it helps the author know what to keep.
  Don't pad the review.
