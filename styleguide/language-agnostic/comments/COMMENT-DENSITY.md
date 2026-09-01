---
type: Styleguide Rule
description: |-
  Aim for 20-30% comment ratio, measured as comment lines divided by
  total non-blank lines. Not every line needs a comment, but every
  function should have documentation and complex sections should have
  explanatory comments.
language: language-agnostic
category: comments
rule_id: COMMENT-DENSITY
priority: info
tags:
- density
- documentation
- maintainability
---
Aim for 20-30% comment ratio, measured as comment lines divided by
total non-blank lines. Not every line needs a comment, but every
function should have documentation and complex sections should have
explanatory comments.

## Good

- // Interpolate between two frames for smooth animation.
// Uses linear interpolation; upgrade to slerp if quality
// demands increase.
void AnimateEntity(entity_t *ent) {
    float frac = GetLerpFraction();
    LerpPosition(ent->prev, ent->curr, frac, &ent->origin);
    LerpAngles(ent->prev, ent->curr, frac, &ent->angles);
    UpdateVisuals(ent);
}


## Bad

- void AnimateEntity(entity_t *ent) {
    float frac = GetLerpFraction();
    LerpPosition(ent->prev, ent->curr, frac, &ent->origin);
    LerpAngles(ent->prev, ent->curr, frac, &ent->angles);
    UpdateVisuals(ent);
}

