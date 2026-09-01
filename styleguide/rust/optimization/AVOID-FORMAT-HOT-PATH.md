---
type: Styleguide Rule
description: |-
  String formatting (format!, println!) is expensive. Avoid in
  performance-critical code or use faster alternatives.
language: rust
category: optimization
rule_id: AVOID-FORMAT-HOT-PATH
priority: warn
tags:
- optimization
- strings
- formatting
---
String formatting (format!, println!) is expensive. Avoid in
performance-critical code or use faster alternatives.

## Good

- // Format once, reuse
let msg = format!("Error: {}", error);
for _ in 0..1000 { log(&msg); }

## Bad

- for _ in 0..1000 {
    log(&format!("Error: {}", error)); // Format in loop
}
