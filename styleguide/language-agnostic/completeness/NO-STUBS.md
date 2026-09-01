---
type: Styleguide Rule
description: |-
  Every function must contain a real implementation. If you cannot
  implement a function, split the file, reduce scope, or ask a
  clarifying question — never write a stub.

  Forbidden patterns by language:
    Rust: todo!(), unimplemented!(), empty impl blocks.
    Python: pass as a function body, raise NotImplementedError,
      ... (ellipsis) as a function body, placeholder returns with
      TODO comments.
    TypeScript: throw new Error("Not implemented"), return {} as T,
      empty function bodies with TODO comments.
    Shell: : (no-op command), return 0 with TODO comment, empty
      function bodies.
    Universal: any function body that is only a TODO comment plus a
      placeholder return value (null, None, 0, "", false, {}, []).

  A build passing is not evidence of completeness. todo!() compiles
  in Rust, pass runs in Python, throw new Error() is valid
  TypeScript. These all defer failure to runtime or silently do
  nothing.

  Note: TODO comments within otherwise complete implementations are
  acceptable (see TODO-WITH-CONTEXT in comments.yaml). What is
  forbidden is using a TODO comment as a substitute for implementing
  the function body.
language: language-agnostic
category: completeness
rule_id: NO-STUBS
priority: error
tags:
- completeness
- stubs
- placeholders
- implementation
- quality
- anti-pattern
---
Every function must contain a real implementation. If you cannot
implement a function, split the file, reduce scope, or ask a
clarifying question — never write a stub.

Forbidden patterns by language:
  Rust: todo!(), unimplemented!(), empty impl blocks.
  Python: pass as a function body, raise NotImplementedError,
    ... (ellipsis) as a function body, placeholder returns with
    TODO comments.
  TypeScript: throw new Error("Not implemented"), return {} as T,
    empty function bodies with TODO comments.
  Shell: : (no-op command), return 0 with TODO comment, empty
    function bodies.
  Universal: any function body that is only a TODO comment plus a
    placeholder return value (null, None, 0, "", false, {}, []).

A build passing is not evidence of completeness. todo!() compiles
in Rust, pass runs in Python, throw new Error() is valid
TypeScript. These all defer failure to runtime or silently do
nothing.

Note: TODO comments within otherwise complete implementations are
acceptable (see TODO-WITH-CONTEXT in comments.yaml). What is
forbidden is using a TODO comment as a substitute for implementing
the function body.

## Good

- // Rust: complete implementation
fn parse_header(input: &[u8]) -> Result<Header, ParseError> {
    let version = input.get(0).copied()
        .context(MissingVersionSnafu)?;
    let length = u16::from_be_bytes(
        input.get(1..3).context(TruncatedSnafu)?.try_into().unwrap()
    );
    Ok(Header { version, length })
}

- # Python: complete implementation
def calculate_discount(price: float, tier: str) -> float:
    """Return discounted price based on customer tier."""
    rates = {"gold": 0.20, "silver": 0.10, "bronze": 0.05}
    rate = rates.get(tier, 0.0)
    return price * (1.0 - rate)

- // TypeScript: complete implementation
function formatCurrency(cents: number): string {
  if (cents < 0) throw new RangeError("cents must be non-negative");
  const dollars = Math.floor(cents / 100);
  const remainder = cents % 100;
  return `$${dollars}.${String(remainder).padStart(2, "0")}`;
}


## Bad

- // Rust: stub with todo!()
fn parse_header(input: &[u8]) -> Result<Header, ParseError> {
    todo!()
}

- // Rust: stub with unimplemented!()
fn connect(addr: &str) -> Result<Connection, Error> {
    unimplemented!()
}

- # Python: stub with pass
def calculate_discount(price: float, tier: str) -> float:
    """Return discounted price based on customer tier."""
    pass

- # Python: stub with ellipsis
def calculate_discount(price: float, tier: str) -> float:
    ...

- # Python: stub with NotImplementedError
def connect(host: str, port: int) -> Connection:
    raise NotImplementedError

- // TypeScript: stub with throw
function formatCurrency(cents: number): string {
  // TODO: implement formatting
  throw new Error("Not implemented");
}

- // TypeScript: stub with type cast
function getUser(id: string): User {
  // TODO: fetch from database
  return {} as User;
}

- # Shell: stub with no-op
process_logs() {
  : # TODO implement
}

