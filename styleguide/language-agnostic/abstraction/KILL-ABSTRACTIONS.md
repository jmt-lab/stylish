---
type: Styleguide Rule
description: |-
  It is not uncommon for the cost of an abstraction to outweigh the
  benefit it delivers. Look for opportunities to simplify by removing
  layers of indirection. Each layer makes code harder to understand —
  keep the number of layers small. Don't build frameworks on frameworks.
language: language-agnostic
category: abstraction
rule_id: KILL-ABSTRACTIONS
priority: warn
tags:
- simplicity
- abstraction
- complexity
- layers
- indirection
---
It is not uncommon for the cost of an abstraction to outweigh the
benefit it delivers. Look for opportunities to simplify by removing
layers of indirection. Each layer makes code harder to understand —
keep the number of layers small. Don't build frameworks on frameworks.

## Good

- // Direct, simple
void Process(Entity* e) { e->x += 1; }
- // Direct: 1-2 layers
app -> renderer -> graphics API

## Bad

- // Over-abstracted
EntityProcessor<DefaultPolicy, HeapAllocator>::Process()
- // Too many layers: 5+ layers
app -> facade -> adapter -> wrapper -> bridge -> API
