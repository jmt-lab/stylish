---
type: Skill
name: rust-port
description: >-
  Port code from C, C++, Python, Go, JavaScript, or TypeScript into idiomatic Rust that
  keeps the original behavior and follows the stylish Rust styleguide: ownership instead
  of manual memory, SNAFU Result errors instead of error codes and exceptions, enums
  instead of flag ints and magic strings, and tests that prove the port matches. Use this
  whenever the user asks to port, translate, convert, migrate, or rewrite code in Rust.
  Pairs with the rust-best-practices skill, which covers the target code's style.
---

# Rust port

The goal is the Rust a Rust developer would have written to solve the same problem, with
the same observable behavior. A line-by-line transliteration compiles but keeps every
problem the original had and adds the borrow checker on top. Port the behavior, not the
structure (RUST-SHAPED-CODE).

## 1. Understand the original before writing anything

1. **Read the code and its tests**, and its callers if you have them.
2. **List the observable behavior:** every public function, its inputs and outputs, and
   every way it can fail. Include the quiet parts, which are where ports go wrong:
   ordering, tie-breaking, empty input, whitespace and case handling, integer limits, and
   what counts as an error versus a valid edge case.
3. **Note what is incidental:** manual memory management, out-parameters, `NULL`
   returns, global state, fixed-size buffers, classes that only group functions, and
   `isinstance` checks. These don't carry over.
4. **Keep bugs and ambiguities as they are.** Flag them in the porting notes and let the
   user decide. Don't silently fix them.

## 2. Port the tests first

Translate the original tests into Rust tests before porting the implementation. Write one
Rust test per original test, named `test_<function>_<scenario>_<expected>`
(DESCRIPTIVE-TEST-NAMES) so each maps back to its original, and structure each with
Arrange-Act-Assert (AAA-PATTERN). If the original has no tests, write characterization
tests from the behavior list.

## 3. Design the Rust API, then implement it

Decide the public types and signatures from the behavior list, not from the original's
shape. Then implement against the ported tests.

### From C and C++

| In the original | In Rust |
|---|---|
| `malloc`/`free`, `new`/`delete`, `create`/`destroy` pairs | Owned types dropped automatically; `Drop` for anything else |
| `NULL` meaning "absent" | `Option<T>` (NO-SENTINEL-VALUES) |
| Error codes, `errno` | `Result<T, E>` with a SNAFU error enum, one variant per failure, with context fields (USE-SNAFU) |
| Out-parameters | Return values (RETURN-VALUES-NOT-OUT-PARAMS) |
| Flag bitmasks | An options struct with `Default`, or `bitflags` (BITFLAGS-FOR-INDEPENDENT-FLAGS) |
| `char *` plus length, `strcmp`, `strcasecmp` | `&str`/`String`, `==`, `eq_ignore_ascii_case` |
| Pointer plus count | Slices and iterators |
| Fixed-size buffers | Growable types; drop the limit unless the limit is behavior |
| `#define` constants and macros | `const`, enums, and functions (NAMED-CONSTANTS) |
| Global mutable state | A struct the caller owns (AVOID-GLOBAL-MUTABLE-STATE) |
| `strtol` and friends | `str::parse` with `.context(..)` into your error enum |

Don't write `unsafe` or use raw pointers unless the port must call C, and then follow
FFI-SAFE-BOUNDARY and ENCAPSULATE-UNSAFE.

### From Python

| In the original | In Rust |
|---|---|
| Exception hierarchy | A SNAFU error enum with one variant per exception class; attributes become fields |
| `None` | `Option<T>` |
| Strings used as a closed set | An enum with `FromStr` and `Display` (IMPLEMENT-STD-TRAITS) |
| Dicts or classes used as records | Structs with named fields (NAMED-FIELDS-OVER-TUPLES) |
| `dict` insertion order | `Vec`, `BTreeMap`, or `IndexMap` when order is observable (DETERMINISTIC-OUTPUT-ORDER) |
| Duck typing, `isinstance` | Traits or enums |
| Unbounded `int` | A sized integer chosen on purpose, with `checked_*` where input can be large |
| `sorted(..., key=...)` | `sort_by_key` / `sort_by` (both stable) |
| `splitlines()`, `strip()`, `isalnum()` | `lines()`, `trim()`, `char` methods; check `\r\n`, Unicode, and empty strings against the original |

### From Go, JavaScript, and TypeScript

- **Go:** `(value, error)` becomes `Result`, `nil` becomes `Option`, and interfaces
  become traits. Goroutines and channels become threads with `mpsc` or async tasks,
  depending on what the original needs.
- **JavaScript and TypeScript:** `null`/`undefined` become `Option`, thrown errors become
  `Result`, plain objects become structs, and numbers become a sized integer or `f64`
  chosen on purpose.

## 4. Keep the port proportionate

- **Don't reimplement the source language's runtime.** Use std's `lines`, `trim`, and
  `parse`. List exotic-input differences in the notes instead of coding around them.
- **Don't grow the API.** Port the original public surface plus the standard traits Rust
  callers expect: `Debug`, `Clone`, `Display`, `Error` (via SNAFU), `FromStr`, `Default`,
  and `IntoIterator` for collections.
- **Keep the algorithm unless it's wrong**, and say so in the notes when you change it.
- **Check the size.** C and C++ ports usually land near the original's size, and Python
  and JavaScript ports at two to three times. Much more than that usually means one of
  the habits above.

## 5. Verify

```bash
cargo build
cargo test
cargo clippy --all-targets -- -D warnings
```

Every ported test must pass. If you can run the original's tests too, compare results on
the same inputs. A few dozen realistic and edge-case inputs answer the question.

## 6. Write the porting notes

Write a short `PORTING.md` next to the code:

- **API mapping:** each original function or type and its Rust equivalent.
- **Test mapping:** each original test and the Rust test that covers it.
- **Deliberate differences:** what now behaves differently, and why.
- **Preserved quirks:** odd behavior kept on purpose.
- **Verification:** the commands you ran and their results, or a plain statement that
  you couldn't run them.

For the style of the Rust itself, follow the `rust-best-practices` skill and
`styleguide/rust/`.

Adapted from the `rust-port` skill in
[BeautifulRust](https://github.com/morganlinton/BeautifulRust) (MIT, Copyright (c) 2026
Morgan Linton).
