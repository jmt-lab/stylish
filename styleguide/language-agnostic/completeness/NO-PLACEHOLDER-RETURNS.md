---
type: Styleguide Rule
description: |-
  Returning a zero-value (null, None, 0, "", false, {}, []) solely
  to satisfy a type checker while leaving actual logic unimplemented
  is a hidden stub. These are worse than explicit stubs because they
  silently produce wrong behavior at runtime instead of panicking.

  Specifically forbidden:
    - Returning None/null when real data should be computed.
    - Returning 0 or false as a default when actual computation is
      missing.
    - Returning an empty collection when the function should
      populate it.
    - Casting to a target type with as T without real data.

  If a function legitimately returns a zero-value, the surrounding
  logic (guards, branches, documentation) should make clear that the
  zero-value is the correct result, not a placeholder.
language: language-agnostic
category: completeness
rule_id: NO-PLACEHOLDER-RETURNS
priority: error
tags:
- completeness
- hidden-stubs
- return-values
- quality
---
Returning a zero-value (null, None, 0, "", false, {}, []) solely
to satisfy a type checker while leaving actual logic unimplemented
is a hidden stub. These are worse than explicit stubs because they
silently produce wrong behavior at runtime instead of panicking.

Specifically forbidden:
  - Returning None/null when real data should be computed.
  - Returning 0 or false as a default when actual computation is
    missing.
  - Returning an empty collection when the function should
    populate it.
  - Casting to a target type with as T without real data.

If a function legitimately returns a zero-value, the surrounding
logic (guards, branches, documentation) should make clear that the
zero-value is the correct result, not a placeholder.

## Good

- # Python: legitimate None return is documented and intentional
def find_user(user_id: str) -> Optional[User]:
    """Return the User if found, None otherwise."""
    row = db.query("SELECT * FROM users WHERE id = %s", user_id)
    if row is None:
        return None
    return User.from_row(row)

- // Rust: empty Vec is the correct result after real filtering
fn active_users(users: &[User]) -> Vec<&User> {
    users.iter().filter(|u| u.is_active).collect()
}


## Bad

- # Python: hidden stub — returns None instead of computing
def find_user(user_id: str) -> Optional[User]:
    # TODO: query database
    return None

- // TypeScript: hidden stub — returns empty array
function getActiveOrders(userId: string): Order[] {
  // TODO: implement database query
  return [];
}

- // Rust: hidden stub — returns 0 instead of computing
fn calculate_checksum(data: &[u8]) -> u32 {
    // TODO: implement CRC32
    0
}

- // TypeScript: hidden stub — returns false
function validateLicense(key: string): boolean {
  // TODO: check license server
  return false;
}

