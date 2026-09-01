---
type: Styleguide Rule
description: |-
  Track bundle size in CI. Use bundlesize or similar. Prevent
  accidental bloat from dependencies or code changes.
language: typescript
category: practices
rule_id: BUNDLE-SIZE-AWARENESS
priority: info
tags:
- performance
- bundle
- monitoring
---
Track bundle size in CI. Use bundlesize or similar. Prevent
accidental bloat from dependencies or code changes.

## Good

- // CI checks bundle size limits
- // Webpack bundle analyzer in build

## Bad

- // No bundle size tracking
