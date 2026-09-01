---
type: Styleguide Rule
description: |-
  Carmack's Doom 3 achieved 30% comments. Not every line needs comments,
  but every function should have documentation and complex sections
  should have explanatory comments.
language: rust
category: comments
rule_id: COMMENT-DENSITY
priority: info
tags:
- comments
- density
- carmack
---
Carmack's Doom 3 achieved 30% comments. Not every line needs comments,
but every function should have documentation and complex sections
should have explanatory comments.

## Good

- /// Compute the frustum planes from the view-projection matrix.
/// Uses Gribb-Hartmann method for efficient extraction.
fn extract_frustum(vp: &Mat4) -> [Plane; 6] {
    // Left plane: row3 + row0
    let left = vp.row(3) + vp.row(0);
    ...
}


## Bad

- fn extract_frustum(vp: &Mat4) -> [Plane; 6] {
    let left = vp.row(3) + vp.row(0);
    let right = vp.row(3) - vp.row(0);
    // No documentation or explanatory comments
}

