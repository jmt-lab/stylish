---
type: Skill
name: rust-review
description: >-
  Review existing Rust code against the stylish Rust styleguide and produce a prioritized
  report where every finding cites the styleguide rule it breaks and gives a concrete fix.
  Use this whenever the user asks to review, audit, critique, or "check" Rust code, a
  crate, a module, a .rs file, a diff, or a pull request, or asks what is wrong with their
  Rust or how to make it more idiomatic. Pairs with the rust-best-practices skill, which
  covers writing new code.
---

# Rust review

Review Rust code against the rules in `styleguide/rust/`, the same rules the
`rust-best-practices` skill uses for writing code, and report what to change. The output
is a review, not a rewrite. Rewrite code only when the user asks.

Look up a rule's exact wording and examples at `styleguide/rust/<category>/<RULE-ID>.md`,
or with the argosy `search_rules` tool if it is available.

## 1. Decide the scope

- **What to read.** Review exactly what the user pointed at. For a diff, review the
  changed lines and anything they break, not the whole file.
- **Library or application.** Check for `lib.rs`, `pub` items used by other crates, or a
  published `Cargo.toml`. Hold library code to the `api_design`, `traits`, and semver
  rules strictly. Application code gets the simplicity rules instead. State which you
  assumed at the top of the report.
- **Edition and MSRV.** Read them from `Cargo.toml`, so you don't recommend features the
  project can't use.
- **Frameworks.** If the crate depends on `bevy` or `bevy_ecs`, first read
  `skill/rust-best-practices/references/bevy.md` and the `styleguide/rust/bevy/` rules.
  Bevy's conventions (by-value system parameters, the prelude, plain-data components)
  are not findings.

## 2. Run the tools first, if you can

```bash
cargo fmt --check
cargo clippy --all-targets --all-features -- -W clippy::pedantic
cargo test
```

Don't paste raw clippy output. Group repeated warnings into one finding, and skip
pedantic lints that don't matter here. If the tools aren't available, say so and review
by reading.

## 3. What to look for, in priority order

**Correctness and soundness**

- **Undefined behavior:**
  - `unsafe` without `// SAFETY:` (UNSAFE-JUSTIFICATION)
  - transmute tricks or `unsafe impl Send` (NO-TRANSMUTE-SHORTCUTS)
  - unsound safe APIs (NO-UNSOUND-ABSTRACTIONS)
  - an `unsafe fn` without `# Safety` docs (DOCUMENT-UNSAFE-CONTRACTS)
- **Reachable panics:**
  - `unwrap`/`expect` on fallible input (EXPECT-WITH-CONTEXT)
  - indexing after a check (PATTERN-MATCH-OVER-CHECK-UNWRAP)
  - lossy `as` casts (FROM-OVER-AS-CASTS)
- **Broken trait contracts:** a custom `Ord` with a derived `PartialEq`, or a `Hash` that
  disagrees with `Eq` (CONSISTENT-ORD-EQ-HASH).
- **Lock hazards:**
  - a guard held across `.await` (NO-LOCK-ACROSS-AWAIT)
  - a callback called under a lock, or a returned guard (LOCK-SCOPE-DISCIPLINE)
  - recovering a poisoned lock (NO-POISONED-MUTEX-ACCESS)
  - `let _ = guard` (NAMED-DROP-GUARDS)
- **Destructors** that panic, block, or fail (DESTRUCTORS-NEVER-FAIL).
- **Bevy ECS bugs:**
  - overlapping mutable queries (BEVY-DISJOINT-QUERIES)
  - unordered dependent systems or deferred `Commands` read too early
    (BEVY-ORDER-DEPENDENT-SYSTEMS)
  - unwrapped queries (BEVY-NO-UNWRAP-QUERIES)

**Error handling**

- Not using SNAFU, or using `anyhow`/`thiserror` (USE-SNAFU, NO-ANYHOW, NO-THISERROR).
  `Whatever` outside prototypes (SNAFU-WHATEVER-SPARINGLY).
- `.map_err()` instead of context selectors (SNAFU-CONTEXT-SELECTORS). A missing
  backtrace on a variant without a source (SNAFU-BACKTRACE). Vague display messages
  (SNAFU-DISPLAY-MESSAGES).
- `String`, `()`, or `Box<dyn Error>` as an error type (ERROR-TYPES-SPECIFIC,
  ERRORS-SEND-SYNC-STATIC).
- Panics used for expected failures (RESULT-FOR-EXPECTED-ERRORS). `catch_unwind` used as
  control flow (NO-CATCH-UNWIND).

**API design** (strict for libraries)

- **Parameters:**
  - `&String`, `&Vec<T>`, `&Box<T>`, or `&Option<T>` (BORROW-INNER-DATA-PARAMS)
  - a `bool` parameter with unclear meaning (ENUM-OVER-BOOL-PARAMS)
  - a borrow cloned internally (TAKE-OWNERSHIP-BY-VALUE)
  - out-parameters (RETURN-VALUES-NOT-OUT-PARAMS)
- **Visibility:**
  - public fields that should be private (PRIVATE-IMPLEMENTATION)
  - smart pointers in signatures (NO-SMART-POINTERS-IN-PUBLIC-API)
  - leaked dependency types (DONT-LEAK-DEPENDENCY-TYPES)
  - two public paths to one item (SINGLE-PUBLIC-PATH)
- **Missing traits:**
  - `Debug` (DEBUG-ON-PUBLIC-TYPES)
  - `Display` (DISPLAY-FOR-READABLE-TYPES)
  - `Default` beside `new()` (DEFAULT-WITH-NEW)
  - `FromStr` instead of an ad-hoc `from_str` (IMPLEMENT-STD-TRAITS)
  - unredacted secrets (REDACT-SECRETS-IN-DEBUG)
- **Naming:**
  - `get_` getters (GETTER-WITHOUT-GET-PREFIX)
  - wrong `as_`/`to_`/`into_` (CONVERSION-PREFIX-CONVENTIONS)
  - weasel words (AVOID-WEASEL-WORDS)
  - stutter (AVOID-STUTTERING)
- **Evolution:**
  - missing `#[non_exhaustive]` (NON-EXHAUSTIVE-PUBLIC-ENUMS,
    NON-EXHAUSTIVE-PUBLIC-STRUCTS)
  - unsealed traits (SEAL-TRAITS)
  - `const fn` you can't commit to (CONST-FN-COMMITMENT)

**Idiom and clarity**

- Clones that exist only to satisfy the borrow checker (PREFER-BORROW-OVER-CLONE,
  MEM-TAKE-OVER-CLONE).
- Invalid states that the types allow (MAKE-INVALID-STATES-UNREPRESENTABLE,
  NO-SENTINEL-VALUES).
- `+` string building (FORMAT-FOR-CONCATENATION). Iterator chains that should be loops,
  or the reverse (ITERATOR-CHAIN-RESTRAINT, ITERATOR-CHAINS).
- `HashMap` order leaking into output (DETERMINISTIC-OUTPUT-ORDER).
- Deep nesting (LIMIT-NESTING-DEPTH, EARLY-RETURN-GUARDS). Functions that do too much
  (FOCUSED-FUNCTIONS).
- Import violations (NO-GLOB-IMPORTS, NO-NESTED-CROSS-MODULE, QUALIFY-FREE-FUNCTIONS).
- `#![deny(warnings)]` in source (NO-DENY-WARNINGS-IN-SOURCE). `#[allow]` without a
  reason (EXPECT-LINT-WITH-REASON).
- `println!`/`dbg!` in library code (LOG-NOT-PRINT).

**Documentation and tests**

- Missing docs or module docs (PUBLIC-ITEM-DOCS, PRIVATE-ITEM-DOCS, MODULE-LEVEL-DOCS).
  Docs that restate the name (AVOID-OBVIOUS-COMMENTS).
- Undocumented panics (PANIC-JUSTIFICATION). Doc examples that use `unwrap()`
  (DOC-EXAMPLES-USE-QUESTION-MARK). `# Errors` sections or parameter tables are findings
  too (NO-ERROR-DOCS, NO-PARAM-DOCS).
- Logic with no tests. Tautological tests (NO-TAUTOLOGICAL-TESTS). Test names that don't
  follow `test_<fn>_<scenario>_<expected>` (DESCRIPTIVE-TEST-NAMES).

## 4. Write the report

~~~markdown
# Rust review: <what was reviewed>

<One paragraph: what the code does, library or application, overall verdict, and the
single most important thing to fix. Say whether clippy and tests were run.>

## Must fix
### 1. <Short title> (`src/file.rs:42`)
**Rule:** <RULE-ID> (`styleguide/rust/<category>/<RULE-ID>.md`)
**Problem:** <what is wrong and the concrete consequence, one or two sentences>
**Fix:**
```rust
<the smallest code change that fixes it>
```

## Should fix
### 2. ...

## Consider
### 3. ...

## What's already good
- <2 to 4 specific things the code does well>
~~~

How to sort findings:

- **Must fix:** a bug, a soundness hole, a reachable panic, a rule with `priority: error`
  broken on a meaningful path, or an API mistake that becomes a breaking change once
  published.
- **Should fix:** the code works but breaks a `warn` rule at a real cost.
- **Consider:** `info` rules, style, naming, and polish.

Rules for each finding:

- Cite a `file:line` location (or `whole file`) and the rule ID with its path. If a
  problem matches no styleguide rule, cite the clippy lint or upstream source instead and
  say that no styleguide rule covers it.
- Show the fix as code, limited to the lines that change.
- Group repeats: report "eight `unwrap()` calls" once and list the lines.
- Respect intent. Something that looks deliberate and documented goes under Consider,
  with the trade-off.
- Keep it proportionate. Five to ten findings is plenty for a short file. Don't bury a
  real bug among nits.
- "What's already good" is required.

## 5. Offer the lints

If the project lacks a `[lints]` table, end by suggesting
`skill/rust-best-practices/references/lints.md` and `clippy.md` (LINTS-IN-CARGO-TOML). Name
two or three findings from this review that the lints would have caught.
