---
type: Styleguide Rule
description: |-
  Any defeats the purpose of type hints. Use specific types, generics,
  or Protocol instead. Document why if Any is unavoidable.
language: python
category: typing
rule_id: AVOID-ANY
priority: warn
tags:
- any
- safety
- specificity
---
Any defeats the purpose of type hints. Use specific types, generics,
or Protocol instead. Document why if Any is unavoidable.

## Good

- def process(data: dict[str, int]) -> list[str]:
- from typing import Protocol
class Drawable(Protocol):
    def draw(self) -> None: ...

## Bad

- def process(data: Any) -> Any:  # No type safety
