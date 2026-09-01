---
type: Styleguide Rule
description: "Adapt Carmack's SUBSYSTEM-PREFIX to TypeScript modules. Use module \norganization instead of function prefixes. Export from subsystem modules."
language: typescript
category: naming
rule_id: TS-NAMESPACE-PREFIX
priority: info
tags:
- modules
- organization
- modern
---
Adapt Carmack's SUBSYSTEM-PREFIX to TypeScript modules. Use module 
organization instead of function prefixes. Export from subsystem modules.

## Good

- // renderer/scene.ts export function render() {}
- // sound/manager.ts export function startSound() {}
- import { render } from './renderer/scene';

## Bad

- // utils.ts export function R_Render() {} // C-style prefix
- export function S_StartSound() {} // Unnecessary in modules
