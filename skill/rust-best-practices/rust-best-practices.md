---
type: Skill
name: rust-best-practices
description: >-
  Write idiomatic, robust, maintainable Rust that follows the stylish Rust styleguide. Use
  this skill whenever you write, refactor, debug, or explain Rust code: new crates,
  modules, functions, structs, traits, error types, async code, unsafe or FFI code, serde
  types, tracing, Cargo.toml, tests, or rustdoc. Trigger on any mention of Rust, cargo, crates, .rs files,
  the borrow checker, lifetimes, traits, clippy, or rustfmt, even when the user does not
  ask for "best practices" or "idiomatic" code.
---

# Rust best practices

This skill condenses the rules in `styleguide/rust/` (one Markdown file per rule, grouped
by category, each with Good and Bad examples). Rule IDs appear in `CAPS-WITH-DASHES`; when
you need the exact wording or examples, read `styleguide/rust/<category>/<RULE-ID>.md`, or
use the argosy `search_rules` tool if that MCP server is available.

When this file and a styleguide rule disagree, the styleguide rule wins.

## 1. Mindset

- **Write Rust-shaped code** (RUST-SHAPED-CODE). Model errors with `Result`, resources
  with ownership and `Drop`, polymorphism with traits and enums, and absence with
  `Option`. `Deref` to a "base" struct, `Manager`/`Factory` types, and `throw_if_null`
  helpers are smells (NO-DEREF-INHERITANCE, AVOID-WEASEL-WORDS).
- **Make invalid states unrepresentable** (MAKE-INVALID-STATES-UNREPRESENTABLE). Use
  data-carrying enums instead of bool flags and "only valid if" comments, newtypes for
  units and IDs (NEWTYPE-OVER-ALIAS), and fallible constructors that validate once
  (VALIDATED-NEWTYPE-CONSTRUCTORS). Use `Option` for absence, never sentinels
  (NO-SENTINEL-VALUES).
- **Application code is not library code.** Library code (anything with external users)
  follows the `api_design` and `traits` rules strictly. Application code should favor
  simplicity: concrete types, `Vec` return values, and no speculative generality. Error
  handling uses SNAFU in both (USE-SNAFU).
- **Let the tools do the work.** rustfmt owns formatting, clippy owns idiom checks, and
  the compiler owns memory safety. Spend your attention on design.

## 2. Before you hand back code

Run these and fix everything they report:

```bash
cargo fmt
cargo clippy --all-targets --all-features -- -D warnings
cargo test
cargo doc --no-deps
```

- Fix a lint instead of silencing it. When a lint is genuinely wrong for one item, use
  `#[expect(clippy::name, reason = "...")]` on the narrowest item (EXPECT-LINT-WITH-REASON).
- Never put `#![deny(warnings)]` in source (NO-DENY-WARNINGS-IN-SOURCE). Enforce it in CI
  instead (DENY-WARNINGS-CI).
- Configure lints once in `Cargo.toml` (LINTS-IN-CARGO-TOML). If a project has none,
  offer `skill/rust-best-practices/references/lints.md` and
  `skill/rust-best-practices/references/clippy.md`. Declare custom cfgs so typos warn
  (DECLARE-CHECK-CFG).

## 3. Ownership and borrowing

- **Prefer unique ownership** (AVOID-RC-WHEN-POSSIBLE, INTERIOR-MUTABILITY-RARE).
  `Rc`/`Arc` and `RefCell`/`Mutex` are legitimate, but only on purpose.
- **Don't clone to satisfy the borrow checker** (PREFER-BORROW-OVER-CLONE). Try these
  first, in this order:
  1. Shorten a borrow with a block, or extend a temporary with a named `let`.
  2. Move a value out with `mem::take`, `mem::replace`, or `Option::take`
     (MEM-TAKE-OVER-CLONE).
  3. Split a large struct so disjoint parts can be borrowed separately
     (SPLIT-STRUCTS-FOR-BORROWS).
  4. Clone small immutable data deliberately.
  5. As a last resort, use indices into an owning `Vec`, or `Rc`/`Weak`.
- **Accept the most general borrow** (BORROW-INNER-DATA-PARAMS, SLICE-OVER-VEC,
  STRING-SLICE-PARAMS): `&str`, `&[T]`, `&T`, `Option<&T>`. `impl AsRef<Path>` is fine on
  parameters but never on fields (ASREF-PARAMS-NOT-FIELDS).
- **Take ownership by value only when you need it** (TAKE-OWNERSHIP-BY-VALUE). Never take
  `&T` and then clone it internally. Return values instead of using out-parameters
  (RETURN-VALUES-NOT-OUT-PARAMS).
- **Prefer owned struct fields** (PREFER-OWNED-STRUCT-FIELDS). Let elision handle
  lifetimes where it can and write `'_` in type paths (RELY-ON-LIFETIME-ELISION). Give the
  explicit ones on types descriptive names (DESCRIPTIVE-LIFETIMES).
- **Return `Cow`** when a function usually passes input through and only sometimes
  allocates (COW-FOR-CONDITIONAL-OWNERSHIP). Store data that never grows as `Box<[T]>`,
  `Box<str>`, or `Arc<str>` (BOXED-SLICE-FOR-FROZEN-DATA).
- **Freeze after setup** with `let data = data;` (FREEZE-AFTER-SETUP).
- **Keep smart pointers out of public signatures** (NO-SMART-POINTERS-IN-PUBLIC-API).
  For a service that must be shared, put `Arc<Inner>` inside it (CHEAP-CLONE-SERVICES).

## 4. Types and API design

### Naming

- Use `UpperCamelCase` for types and variants, `snake_case` for functions, modules, and
  locals, and `SCREAMING_SNAKE_CASE` for consts. Acronyms count as one word: `HttpClient`,
  `Uuid` (ACRONYMS-AS-WORDS).
- Accessors (GETTER-WITHOUT-GET-PREFIX, SETTER-WITH-SET-PREFIX, ACCESSOR-NAMING): `foo()`,
  `foo_mut()`, `set_foo()`, `take_foo()`, `replace_foo()`, `with_foo(|f| ..)`.
- Conversions (CONVERSION-PREFIX-CONVENTIONS): `as_` is free (borrow to borrow), `to_`
  does work, and `into_` consumes `self`.
- Constructors (CONSTRUCTOR-NAMING): `new`, `new_with_foo`, `try_new` when fallible, and
  `from_foo` paired with a `From` impl (PAIR-FROM-WITH-CONSTRUCTOR).
- Iterator types share the name of the method that returns them: `Iter`, `IterMut`,
  `IntoIter`, `Keys` (ITERATOR-TYPE-NAMES).
- Error types read verb-object-error: `ParseConfigError` (ERROR-TYPE-WORD-ORDER).
- Avoid weasel words like `Manager`, `Service`, `Factory`, and `Util` (AVOID-WEASEL-WORDS).
  Don't stutter the module name (AVOID-STUTTERING). Avoid obscure abbreviations
  (AVOID-ABBREVIATIONS).
- Extension traits end in `Ext` (EXTENSION-TRAIT-EXT-SUFFIX).

### Model the domain

- Use enums instead of `bool` parameters whose meaning isn't obvious
  (ENUM-OVER-BOOL-PARAMS).
- Use named fields instead of tuples (NAMED-FIELDS-OVER-TUPLES).
- Use the strongest std type, such as `Path`, `Duration`, or `SocketAddr`
  (STRONGEST-STD-TYPE).
- Use `bitflags` for independent flags (BITFLAGS-FOR-INDEPENDENT-FLAGS).
- Use enums, newtypes, and parsed types instead of strings for closed sets, IDs, and
  structured text (NO-STRINGLY-TYPED-APIS).
- Encode ordered protocols (connect, then log in, then query) as typestates when misuse is
  a real risk (TYPESTATE-FOR-PROTOCOLS).
- Convert with `From`/`TryFrom` rather than `as` (FROM-OVER-AS-CASTS).

### Numbers

- Make overflow intent explicit on unbounded input with `checked_*`, `saturating_*`,
  `clamp`, or `wrapping_*` (EXPLICIT-OVERFLOW-HANDLING).
- Never compare computed floats with `==`. Use a tolerance, and sort with `total_cmp`
  (NO-FLOAT-EQUALITY).

### Standard traits

- Derive rather than hand-write (PREFER-DERIVE).
- Every public type implements `Debug` (DEBUG-ON-PUBLIC-TYPES). Types holding secrets
  redact it (REDACT-SECRETS-IN-DEBUG).
- Implement `Display` for anything people read (DISPLAY-FOR-READABLE-TYPES).
- Implement `Clone` for most types and `Copy` for small stable ones
  (IMPLEMENT-CLONE-BY-DEFAULT). Add `Hash`, `Eq`, and `Ord` for key-like types
  (MAP-KEY-TRAITS).
- Provide `Default` next to `new()` (DEFAULT-WITH-NEW) and on options structs
  (OPTIONS-STRUCT-DEFAULT).
- Hand-written `Ord`, `PartialEq`, and `Hash` must agree (CONSISTENT-ORD-EQ-HASH).
- Implement std traits instead of ad-hoc methods, e.g. `FromStr` (IMPLEMENT-STD-TRAITS).
  Implement `From`, never `Into` (IMPL-FROM-NOT-INTO), and `TryFrom` for fallible
  conversions instead of `from_x() -> Option` (TRYFROM-FOR-FALLIBLE-CONVERSIONS).
- Collections get `FromIterator`, `Extend`, and `IntoIterator` (COLLECTION-TRAITS).
- Put no trait bounds on struct definitions (NO-STRUCT-TRAIT-BOUNDS).
- Overload operators only for their mathematical meaning (OPERATOR-OVERLOAD-MATH-ONLY).
- Use `#[must_use]` where ignoring the result is a bug (MUST-USE-FUNCTIONS,
  MUST-USE-TYPES).

### Construction

- With four or more fields or options, use `bon::Builder` or `Default`
  (PREFER-BUILDER-PATTERN). Don't use bon for newtypes (AVOID-BON-NEWTYPES).
- Setters are infallible; validation lives in a fallible build or constructor
  (BUILDER-VALIDATES-IN-BUILD).

### Visibility and evolution (libraries)

- Keep things private by default (PRIVATE-IMPLEMENTATION, VISIBILITY-INTENTIONAL).
- Expose each item at a single path (SINGLE-PUBLIC-PATH).
- Don't leak third-party types (DONT-LEAK-DEPENDENCY-TYPES).
- Use `#[non_exhaustive]` on public enums and public-field structs
  (NON-EXHAUSTIVE-PUBLIC-ENUMS, NON-EXHAUSTIVE-PUBLIC-STRUCTS).
- Seal traits that outsiders shouldn't implement (SEAL-TRAITS).
- Make a function `const` only if it will stay const (CONST-FN-COMMITMENT).

### Traits and generics

- Define a trait only for polymorphism or extension (TRAITS-FOR-POLYMORPHISM-ONLY), and
  keep essential functionality in inherent methods (ESSENTIAL-FUNCTIONALITY-INHERENT).
- Prefer concrete types, then generics, then wrapped `dyn`
  (PREFER-CONCRETE-THEN-GENERIC-THEN-DYN, GENERICS-OVER-DYN-IN-LIBRARIES). Don't nest
  generics on services (NO-NESTED-GENERIC-SERVICES).
- Decide object safety early (DECIDE-OBJECT-SAFETY-EARLY). Keep required methods minimal
  and give the rest defaults (MINIMAL-REQUIRED-TRAIT-METHODS).
- Use an associated type when each impl has exactly one choice, and a generic parameter
  when one type implements the trait many ways (ASSOCIATED-TYPE-VS-GENERIC-PARAMETER).
  Wrap foreign types in a newtype to implement foreign traits (NEWTYPE-FOR-FOREIGN-TRAITS).
- Use the most general `Fn*` bound, with the closure as the last parameter
  (CLOSURE-BOUNDS-MOST-GENERAL). Return closures as `impl Fn`, not `Box<dyn Fn>`
  (RETURN-IMPL-FN).
- Libraries return iterators and accept `impl IntoIterator`
  (RETURN-ITERATORS-IN-LIBRARIES, ACCEPT-INTOITERATOR-IN-LIBRARIES). Use `impl Into<T>`
  sparingly (IMPL-INTO-SPARINGLY). Accept `impl RangeBounds` (RANGEBOUNDS-PARAMS) and
  `impl Read`/`impl Write` (ACCEPT-READ-WRITE).
- Reach for functions, types, and traits before `macro_rules!`, and `macro_rules!` before
  proc macros (PREFER-FUNCTIONS-OVER-MACROS, MACROS-DONT-LIE, MACRO-HYGIENE).
  `macro_rules!` uses `$crate::` and `::core::` paths (MACRO-DOLLAR-CRATE-PATHS) and
  precise fragment specifiers (MACRO-FRAGMENT-SPECIFIERS). Proc macros report spanned
  `syn::Error`s and never panic (PROC-MACRO-SPANNED-ERRORS).

### Refactoring someone else's code

- Fix every smell the request is about, not just the cheap ones.
- Keep public behavior identical unless changing it is the point. Preserve quirks you
  don't understand and flag them.
- If the module has no tests, pin its behavior with characterization tests before you
  touch it (FAILING-TEST-BEFORE-FIX).

## 5. Errors and panics

| Situation | Use |
|---|---|
| Absence is normal | `Option<T>` (OPTION-FOR-ABSENCE) |
| Expected failure the caller may handle | `Result<T, E>` (RESULT-FOR-EXPECTED-ERRORS) |
| A bug or violated invariant | `panic!` / `assert!` / `expect("why")` (PANIC-FOR-PROGRAMMER-ERRORS) |

- **SNAFU is required** (USE-SNAFU). Use `anyhow` and `thiserror` nowhere (NO-ANYHOW,
  NO-THISERROR), and `Whatever` only for prototypes (SNAFU-WHATEVER-SPARINGLY).
- Add context at each error site with context selectors and `.context()`, never
  `.map_err()` (SNAFU-CONTEXT-SELECTORS).
- Variants without a source get a backtrace field (SNAFU-BACKTRACE).
- Display messages say what failed and include the relevant values
  (SNAFU-DISPLAY-MESSAGES).
- Make error types specific (ERROR-TYPES-SPECIFIC) and `Send + Sync + 'static`
  (ERRORS-SEND-SYNC-STATIC). Never use `()`, `String`, or `Box<dyn Error>` as a public
  error type.
- If a fallible function consumes its argument, return the argument in the error
  (RETURN-CONSUMED-ARG-ON-ERROR).
- Use `expect` only for invariants, with a message that says why the invariant holds
  (EXPECT-WITH-CONTEXT). Pattern-match instead of check-then-unwrap
  (PATTERN-MATCH-OVER-CHECK-UNWRAP). Give assertions context messages
  (ASSERT-CONTEXT-MESSAGES, PANIC-WITH-MESSAGE).
- Never discard an error with `let _ =`, `.ok()`, or an empty `Err` arm without a
  comment explaining why (NEVER-SILENTLY-DISCARD-ERRORS).
- A poisoned lock is fatal; never use `into_inner` (NO-POISONED-MUTEX-ACCESS).
- Never use `catch_unwind` for control flow (NO-CATCH-UNWIND).
- Destructors never fail, panic, or block; provide `close()` (DESTRUCTORS-NEVER-FAIL).
- Pair a panicking convenience method with a fallible one (PAIR-PANICKING-WITH-FALLIBLE).
- Don't write `# Errors` doc sections; the error type documents the failure modes
  (NO-ERROR-DOCS). Do document panics (PANIC-JUSTIFICATION).

## 6. Everyday idioms

- Use short iterator chains over hand loops (ITERATOR-CHAINS), but switch to a `for` loop
  when a chain branches or mutates outside state (ITERATOR-CHAIN-RESTRAINT). Collect
  fallible steps into `Result<Vec<_>, _>` (COLLECT-INTO-RESULT).
- Use `Option`/`Result` combinators where they are clearer than `match`
  (OPTION-COMBINATORS).
- Use guard clauses: `let ... else` (LET-ELSE-GUARDS), early returns and `?`
  (EARLY-RETURN-GUARDS, QUESTION-MARK-EARLY).
- Patterns: use `matches!` for boolean tests (MATCHES-MACRO-FOR-BOOLEAN-TESTS), let chains
  instead of nested `if let` (LET-CHAINS), and `@` to bind a matched value (AT-BINDINGS).
- Collections: use `Vec` by default, `VecDeque` or `BinaryHeap` when the access pattern
  calls for them, and never `LinkedList` (VEC-BY-DEFAULT). Pick the map by access pattern
  (CHOOSE-MAP-BY-ACCESS-PATTERN), use sets for membership (SET-FOR-MEMBERSHIP), and the
  entry API for insert-or-update (ENTRY-API).
- Use `const` for inlined values and `static` only for one address or interior mutability
  (CONST-VS-STATIC). Use `const { }` blocks for compile-time values and asserts in
  expressions (INLINE-CONST-BLOCKS).
- Use `format!`/`write!` instead of `+` chains (FORMAT-FOR-CONCATENATION).
- Annotate types where inference hides intent (ANNOTATE-INFERRED-TYPES).
- Bind RAII guards to a name; `let _ =` drops immediately (NAMED-DROP-GUARDS).
- Rebind captures in a block before a `move` closure (CLOSURE-CAPTURE-REBINDING).
- Never let `HashMap` iteration order reach output (DETERMINISTIC-OUTPUT-ORDER).
- Imports:
  - Put them at the top, ordered by rustfmt (IMPORTS-AT-TOP, CARGO-FMT-SORTING).
  - Nest only within one module (NESTED-SAME-MODULE, NO-NESTED-CROSS-MODULE).
  - Use types unqualified and qualify free functions by their module
    (UNQUALIFIED-TYPE-NAMES, QUALIFY-FREE-FUNCTIONS).
  - Import traits locally (LOCAL-TRAIT-IMPORTS).
  - No globs except `super::*` in tests, `Enum::*` in matches, and preludes
    (NO-GLOB-IMPORTS).
- Replace magic numbers with named, documented consts (NAMED-CONSTANTS,
  DOCUMENT-MAGIC-VALUES).
- Log with `tracing` or `log`, not `println!`/`dbg!` (LOG-NOT-PRINT). See section 10 for
  observability.

## 7. Concurrency and async

- Assert `Send`/`Sync` on public types at compile time (ASSERT-SEND-SYNC).
- Prefer message passing (PREFER-MESSAGE-PASSING). Keep lock scopes short, never call
  callbacks under a lock, and never return guards (LOCK-SCOPE-DISCIPLINE). Never hold a
  guard across `.await` (NO-LOCK-ACROSS-AWAIT).
- Write `async fn` (ASYNC-FN-OVER-IMPL-FUTURE), including in traits
  (NATIVE-ASYNC-FN-IN-TRAITS), and take async callbacks as `impl AsyncFn`
  (ASYNC-CLOSURE-BOUNDS).
- Never block the executor: CPU-bound work yields or goes to `spawn_blocking`
  (YIELD-IN-CPU-BOUND-ASYNC), and blocking I/O uses async APIs (NO-BLOCKING-IN-ASYNC).
- Run independent futures with `join!`/`try_join!` (JOIN-INDEPENDENT-FUTURES). Track
  every spawned task in a `JoinHandle` or `JoinSet` (TRACK-SPAWNED-TASKS), give
  long-running tasks a shutdown signal (GRACEFUL-SHUTDOWN), and put a timeout on every
  external await (TIMEOUT-EXTERNAL-AWAITS).
- Only cancel-safe futures race in a looping `select!` (CANCEL-SAFE-SELECT).
- Use bounded channels (BOUNDED-CHANNELS), chosen by pattern: `mpsc`, `oneshot`,
  `broadcast`, or `watch` (CHANNEL-MATCHES-PATTERN).
- Threads: use `thread::scope` to borrow stack data (SCOPED-THREADS-FOR-BORROWS) and
  rayon for data parallelism (RAYON-FOR-DATA-PARALLELISM). Use `Mutex` by default and
  `RwLock` only for measured read-heavy contention (RWLOCK-ONLY-WHEN-READ-HEAVY). Justify
  every atomic `Ordering` (ATOMIC-ORDERING-DELIBERATE).
- Libraries don't spawn threads or assume a runtime (LIBRARIES-DONT-ASSUME-RUNTIME).
- For a whole async service (runtime setup, task layout, shutdown, async tests), use the
  `rust-async` skill.
- Avoid global mutable state (AVOID-GLOBAL-MUTABLE-STATE) and code that runs before
  `main` (NO-CODE-BEFORE-MAIN).

## 8. Unsafe and FFI

- Avoid `unsafe`. When you need it, wrap it in a small safe abstraction and justify it
  (ENCAPSULATE-UNSAFE).
- Every block gets a `// SAFETY:` comment (UNSAFE-JUSTIFICATION) and covers one operation
  (MINIMIZE-UNSAFE-SCOPE). Every `unsafe fn` gets a `# Safety` section
  (DOCUMENT-UNSAFE-CONTRACTS) and uses `unsafe_op_in_unsafe_fn` (UNSAFE-OP-IN-UNSAFE-FN).
- Use `MaybeUninit` for uninitialized memory, never `mem::uninitialized` or `mem::zeroed`
  on types with invalid zero patterns (MAYBEUNINIT-FOR-UNINIT-MEMORY).
- Never use `static mut` (NO-STATIC-MUT).
- Mark a function `unsafe` only when misuse can cause UB (UNSAFE-MEANS-UB).
- Don't use `transmute` tricks or `unsafe impl Send` (NO-TRANSMUTE-SHORTCUTS). Never ship
  an unsound safe API; the module is the soundness boundary (NO-UNSOUND-ABSTRACTIONS).
- Run Miri over unsafe code (MIRI-FOR-UNSAFE).
- FFI uses `repr(C)`, `CString`, RAII handles, null checks, and no unwinding across the
  boundary (FFI-SAFE-BOUNDARY). Bindings live in `-sys` crates (SYS-CRATE-SPLIT).
  Newtypes that cross the boundary are `#[repr(transparent)]`
  (REPR-TRANSPARENT-FFI-NEWTYPES).
- Use Rust 2024 syntax: `unsafe extern` blocks with `safe`/`unsafe` items
  (UNSAFE-EXTERN-BLOCKS), and `#[unsafe(no_mangle)]` with a SAFETY comment
  (UNSAFE-ATTRIBUTES).
- No unstable features (NO-UNSTABLE-FEATURES). Don't touch `#[doc(hidden)]` items you
  don't own (NO-DOC-HIDDEN-ACCESS).

## 9. Crates, modules, dependencies

- Use a flat `crates/` workspace (FLAT-CRATES-WORKSPACE) with shared workspace
  dependencies (CARGO-WORKSPACE-COMMON, CARGO-WORKSPACE-SHORTHAND) and alphabetized deps
  (CARGO-DEPS-ALPHABETIZE).
- Name a module after its primary item (FILE-MATCHES-MODULE, ONE-STRUCT-PER-FILE-COMPLEX).
  Non-leaf modules only declare and re-export (NO-IMPL-IN-NON-LEAF-MODULES,
  PUBLIC-API-MOD-RS).
- Several executables go in `src/bin/` over a shared `lib.rs`
  (SRC-BIN-FOR-MULTIPLE-BINARIES). Crate names carry no `-rs` suffix
  (CRATE-NAME-NO-RS-SUFFIX).
- Features are additive and bare-named (ADDITIVE-FEATURES, BARE-FEATURE-NAMES). Put mocks
  behind `test-util` (TEST-UTIL-FEATURE), and serde support in libraries behind a `serde`
  feature (SERDE-BEHIND-FEATURE).
- Keep `build.rs` small, deterministic, and offline (MINIMAL-BUILD-SCRIPTS). Published
  crates fill in `[package]` metadata (CARGO-PACKAGE-METADATA).
- Use version ranges, never `*` (DEPENDENCY-VERSION-RANGES). Commit `Cargo.lock` for
  binaries (COMMIT-LOCKFILE-FOR-BINARIES). Keep dependencies few
  (MINIMIZE-DEPENDENCIES) and audit them (CARGO-AUDIT-SECURITY, CARGO-DENY).
- Use the latest edition and a deliberate MSRV (LATEST-EDITION-AND-MSRV, MSRV-POLICY).
  Follow semver (SEMVER-ADHERENCE).

## 10. Serialization and observability

- serde:
  - Set the wire naming with one `rename_all` (SERDE-RENAME-ALL).
  - Give fields added later a `default` (SERDE-DEFAULT-FOR-COMPATIBILITY).
  - Skip empty optional fields (SERDE-SKIP-EMPTY-FIELDS).
  - Choose enum tagging on purpose and avoid `untagged` (SERDE-ENUM-TAGGING-DELIBERATE).
  - Deny unknown fields in files you own (SERDE-DENY-UNKNOWN-FIELDS).
  - Validate while deserializing with `try_from` (SERDE-VALIDATE-ON-DESERIALIZE).
  - Customize a single field with `with` (SERDE-WITH-FOR-FOREIGN-FORMATS).
- tracing:
  - Libraries never install a subscriber (LIBRARIES-NEVER-INSTALL-SUBSCRIBERS).
  - Record structured fields with constant messages (STRUCTURED-LOG-FIELDS).
  - Give each request or job a span (INSTRUMENT-UNITS-OF-WORK).
  - Use levels consistently (MEANINGFUL-LOG-LEVELS).
  - Log each error once, with its source chain (LOG-ERRORS-ONCE-WITH-CHAIN).
  - Never log secrets or personal data (NEVER-LOG-SECRETS).

## 11. Documentation and comments

- Document every item, public and private (PUBLIC-ITEM-DOCS, PRIVATE-ITEM-DOCS), and
  every module with `//!` (MODULE-LEVEL-DOCS). Start with a summary line under 120
  characters, followed by a blank line (SUMMARY-LINE-LENGTH, SUMMARY-SEPARATION).
- Write sections in the order Examples, Panics, Safety (DOC-SECTION-ORDER). Don't write
  parameter tables or `# Errors` (NO-PARAM-DOCS, NO-ERROR-DOCS).
- Examples use `?`, never `unwrap()` (DOC-EXAMPLES-USE-QUESTION-MARK), and hide setup
  lines with `# ` (HIDE-DOC-EXAMPLE-SETUP). Use intra-doc links (INTRA-DOC-LINKS).
  Published libraries use the README as crate docs (CRATE-README-AS-DOCS).
- Comments explain why, not what (EXPLAIN-WHY-NOT-WHAT, AVOID-OBVIOUS-COMMENTS).
  TODOs carry context (TODO-WITH-CONTEXT). No design journals (NO-META-DESIGN-DOCS).

## 12. Tests

- Unit tests go in `#[cfg(test)] mod tests` and integration tests in `tests/`
  (INTEGRATION-TEST-LOCATION).
- Name tests `test_<function>_<scenario>_<expected>` (DESCRIPTIVE-TEST-NAMES) and use the
  Arrange-Act-Assert structure (AAA-PATTERN).
- Test properties, not restated constants (NO-TAUTOLOGICAL-TESTS, PROPERTY-BASED-TESTING).
- Write the failing test first when fixing a bug (FAILING-TEST-BEFORE-FIX).
- I/O must be mockable (MOCKABLE-IO, MOCK-DEPENDENCIES). Fuzz untrusted parsers
  (FUZZ-UNTRUSTED-INPUT).
- Test the feature combinations that matter (TEST-FEATURE-COMBINATIONS).
- Write async tests with `#[tokio::test]` and paused time (TOKIO-TEST-FOR-ASYNC).
- Model-check lock-free code with loom (LOOM-FOR-CONCURRENCY-PRIMITIVES).
- Snapshot large output with insta (SNAPSHOT-TESTS-FOR-COMPLEX-OUTPUT).
- Clean up fixtures through `Drop` (RAII-TEST-FIXTURES).
- Benchmark with criterion and `black_box` (BLACK-BOX-IN-BENCHMARKS).

## 13. Performance, in order

Design for usability first, then measure (PROFILE-FIRST, MEASURE-DONT-ASSUME). After
that:

- Use `with_capacity` (CAPACITY-HINTS).
- Reuse buffers (ALLOCATION-CONSCIOUS).
- Use zero-copy parsing (ZERO-COPY-PARSING).
- Box large types (BOX-LARGE-TYPES).
- Reuse allocations with `clone_from` (CLONE-FROM-REUSE).
- Buffer I/O (BUFFERED-IO).
- Inline proven hot paths (INLINE-HOT-PATHS) and mark cold ones `#[cold]`
  (COLD-UNLIKELY-PATHS).
- Use a fast hasher for trusted keys (FAST-HASHER-FOR-TRUSTED-KEYS).
- Use `target-cpu` and PGO only for known hardware (TARGET-CPU-ONLY-FOR-KNOWN-HARDWARE).
- Benchmark critical paths (BENCHMARK-CRITICAL-PATHS).

## 14. Final checklist

- `cargo fmt`, `cargo clippy -- -D warnings`, and `cargo test` are clean.
- There is no `unwrap()` outside tests. Every `expect`, `assert`, and `panic` has a
  message.
- Errors are SNAFU types with context selectors, specific variants, and backtraces.
- Parameters take `&str`, `&[T]`, or `impl IntoIterator`, not `&String` or `&Vec<T>`. No
  public `bool` parameters with unclear meaning.
- Public types derive `Debug` and the applicable common traits.
- No `.clone()` exists only to satisfy the borrow checker.
- No error is silently discarded.
- Async code doesn't block, every spawned task is tracked, and every external await has a
  timeout.
- Every `unsafe` block has a `// SAFETY:` comment and every `unsafe fn` has `# Safety`
  docs.
- Every item has a doc comment with a one-line summary.
- Application code stayed simple; library code followed the API rules.

## Framework notes

- **Bevy:** if `Cargo.toml` depends on `bevy` or `bevy_ecs`, read
  `skill/rust-best-practices/references/bevy.md` and the `styleguide/rust/bevy/` rules
  first. Some general advice is wrong for systems.
- **Tokio services:** use the `rust-async` skill.
- **Reviewing existing Rust:** use the `rust-review` skill, which ranks findings by these
  rules' priorities.

## Sources

The rules in `styleguide/rust/` tagged `beautiful-rust` were distilled from
[BeautifulRust](https://github.com/morganlinton/BeautifulRust) (MIT, Copyright (c) 2026
Morgan Linton). That project synthesizes the Google Rust Style Guide, the Rust API
Guidelines, Effective Rust, Rust Design Patterns, and Microsoft's Pragmatic Rust
Guidelines. Rules tagged `google-style` come directly from the Google Rust Style Guide.
Rules tagged `rust-skills` were distilled from
[rust-skills](https://github.com/leonardomso/rust-skills) (MIT, Copyright (c) 2025 Leonardo Maldonado).
Rust-skills rules that conflict with house rules were not merged: thiserror for
libraries, anyhow for applications, `# Errors` doc sections, single-letter lifetimes and
type parameters, `impl Into<T>` everywhere, `#![deny(...)]` in source, and nightly-only
APIs.

Where those sources conflict with this styleguide's house rules (SNAFU instead of
anyhow/thiserror, no `# Errors` docs, preludes allowed), the house rules win.
