---
type: Styleguide Rule
description: "Callback functions and event handlers should use on or handle prefix \nto make their purpose clear."
language: typescript
category: naming
rule_id: TS-CALLBACK-SUFFIX
priority: info
tags:
- callbacks
- events
- clarity
---
Callback functions and event handlers should use on or handle prefix 
to make their purpose clear.

## Good

- function onEntitySpawn(entity: Entity) {}
- const handleClick = () => {};
- element.addEventListener('click', onClick);

## Bad

- function entitySpawn() {} // Unclear it's a callback
- const click = () => {}; // Ambiguous
