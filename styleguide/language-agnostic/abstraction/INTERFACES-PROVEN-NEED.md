---
type: Styleguide Rule
description: |-
  Don't create interfaces 'just in case'. Add polymorphism when you
  have multiple concrete implementations that need to be swappable.
language: language-agnostic
category: abstraction
rule_id: INTERFACES-PROVEN-NEED
priority: warn
tags:
- interfaces
- polymorphism
- abstraction
---
Don't create interfaces 'just in case'. Add polymorphism when you
have multiple concrete implementations that need to be swappable.

## Good

- // Two real implementations
class IRenderer { };
class D3DRenderer : IRenderer { };
class VulkanRenderer : IRenderer { };

## Bad

- // Only one implementation, no need for interface
class IGameManager { };
class GameManager : IGameManager { };
