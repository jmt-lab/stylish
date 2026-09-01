---
type: Styleguide Rule
description: |-
  Keep I/O and side effects at system boundaries. Core logic should be
  pure functions. This makes testing easier and logic more reusable.
language: python
category: functional
rule_id: SIDE-EFFECT-ISOLATION
priority: error
tags:
- side-effects
- architecture
- purity
---
Keep I/O and side effects at system boundaries. Core logic should be
pure functions. This makes testing easier and logic more reusable.

## Good

- def process(data: Data) -> Result:  # Pure
    return transform(data)

def main():
    data = read_file()
    result = process(data)
    write_file(result)

## Bad

- def process(data: Data) -> Result:
    log("Processing")  # Side effect
    result = transform(data)
    update_cache(result)  # Side effect
    return result
