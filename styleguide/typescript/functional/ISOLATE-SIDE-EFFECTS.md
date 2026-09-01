---
type: Styleguide Rule
description: |-
  Keep side effects (I/O, mutations, logging) at system boundaries.
  Core logic should be pure transformations.
language: typescript
category: functional
rule_id: ISOLATE-SIDE-EFFECTS
priority: warn
tags:
- side-effects
- architecture
- boundaries
---
Keep side effects (I/O, mutations, logging) at system boundaries.
Core logic should be pure transformations.

## Good

- // Pure core
function process(data: Data): Result

// Side effects at boundary
async function main() {
  const data = await readFile();
  const result = process(data);
  await writeFile(result);
}

## Bad

- function process(data: Data): Result {
  console.log('processing');
  updateGlobalState();
  return transform(data);
}
