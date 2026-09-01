---
type: Styleguide Rule
description: |-
  If code works around bugs in libraries, browsers, or TypeScript itself,
  document what the issue is and when it can be removed.
language: typescript
category: comments
rule_id: WORKAROUND-DOCUMENTATION
priority: error
tags:
- workarounds
- bugs
- maintenance
---
If code works around bugs in libraries, browsers, or TypeScript itself,
document what the issue is and when it can be removed.

## Good

- // Workaround for TypeScript 4.9 inference bug with generic constraints // Can be removed after upgrading to TS 5.0+
- // React 18 strict mode calls effects twice in dev // This flag prevents duplicate API calls

## Bad

- // Hack for weird bug if (specialCase)
