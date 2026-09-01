---
type: Styleguide Rule
description: |-
  Define interfaces with Protocol instead of abstract base classes when
  you only care about behavior, not inheritance.
language: python
category: typing
rule_id: PROTOCOL-STRUCTURAL
priority: info
tags:
- protocol
- interfaces
- duck-typing
---
Define interfaces with Protocol instead of abstract base classes when
you only care about behavior, not inheritance.

## Good

- from typing import Protocol
class Renderable(Protocol):
    def render(self) -> None: ...

## Bad

- from abc import ABC
class Renderable(ABC):  # Forces inheritance
