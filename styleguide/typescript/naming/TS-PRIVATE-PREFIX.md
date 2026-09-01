---
type: Styleguide Rule
description: |-
  Prefer ECMAScript private fields (#) over both the underscore prefix
  convention (_field) and the TypeScript private keyword (private field).
  The # syntax provides true runtime privacy enforced by the language,
  whereas underscore is merely a naming convention with no enforcement,
  and the TypeScript private keyword is erased at compile time.
language: typescript
category: naming
rule_id: TS-PRIVATE-PREFIX
priority: info
tags:
- classes
- privacy
- modern
---
Prefer ECMAScript private fields (#) over both the underscore prefix
convention (_field) and the TypeScript private keyword (private field).
The # syntax provides true runtime privacy enforced by the language,
whereas underscore is merely a naming convention with no enforcement,
and the TypeScript private keyword is erased at compile time.

## Good

- class Entity { #id: number; }
- class Renderer { #context: WebGLContext; }

## Bad

- class Entity { _id: number; } // Underscore convention
- class Entity { private id: number; } // Weaker than #
