---
type: Styleguide Rule
description: |-
  Complex or non-obvious APIs should include @example blocks showing
  typical usage patterns.
language: typescript
category: comments
rule_id: EXAMPLE-FOR-COMPLEX
priority: info
tags:
- tsdoc
- examples
- usability
---
Complex or non-obvious APIs should include @example blocks showing
typical usage patterns.

## Good

- /**
 * @example
 * const result = await retry(() => fetchData(), {
 *   maxAttempts: 3,
 *   backoff: 'exponential'
 * });
 */

