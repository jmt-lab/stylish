---
type: Styleguide Rule
description: |-
  Use @param, @returns, and @throws tags in TSDoc. Focus on non-obvious
  constraints, not just restating the type signature.
language: typescript
category: comments
rule_id: PARAM-RETURNS-THROWS
priority: warn
tags:
- tsdoc
- parameters
- contracts
---
Use @param, @returns, and @throws tags in TSDoc. Focus on non-obvious
constraints, not just restating the type signature.

## Good

- /**
 * @param buffer - Must be at least 256 bytes
 * @returns Parsed entity or null if buffer is malformed
 * @throws {ValidationError} When buffer contains invalid UTF-8
 */


## Bad

- /**
 * @param buffer - The buffer
 * @returns The result
 */

