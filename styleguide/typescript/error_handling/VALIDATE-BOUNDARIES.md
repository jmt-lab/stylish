---
type: Styleguide Rule
description: |-
  Validate all external input (API responses, user input, file data) at
  boundaries. Use runtime validation libraries (zod, io-ts) for external
  data — TypeScript types alone don't validate runtime values. Never trust
  external data.
language: typescript
category: error_handling
rule_id: VALIDATE-BOUNDARIES
priority: error
tags:
- validation
- security
- boundaries
- runtime-safety
- schemas
---
Validate all external input (API responses, user input, file data) at
boundaries. Use runtime validation libraries (zod, io-ts) for external
data — TypeScript types alone don't validate runtime values. Never trust
external data.

## Good

- function parseInput(raw: unknown): Result<Input, ValidationError> { ... }
- const validated = schema.safeParse(apiResponse);
- if (typeof value !== 'number' || value < 0) return { ok: false, error: ... };
- const ConfigSchema = z.object({ port: z.number() });
- const result = ConfigSchema.safeParse(data);
if (!result.success) return { ok: false, error: result.error };

## Bad

- const data = JSON.parse(input) as MyType; // No validation
- const config = data as Config; // No runtime validation
