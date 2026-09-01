---
type: Styleguide Rule
description: |-
  Functions should use lowercase prefixes indicating their subsystem.
  This makes ownership and responsibility immediately clear when reading code.
language: language-agnostic
category: naming
rule_id: SUBSYSTEM-PREFIX
priority: warn
tags:
- functions
- organization
- clarity
---
Functions should use lowercase prefixes indicating their subsystem.
This makes ownership and responsibility immediately clear when reading code.

## Good

- R_RenderScene() // Renderer subsystem
- S_StartSound() // Sound subsystem
- CL_ReadPackets() // Client subsystem
- SV_Frame() // Server subsystem

## Bad

- RenderScene() // No prefix, unclear ownership
- startSound() // No prefix
