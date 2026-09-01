---
type: Styleguide Rule
description: |-
  Often the best optimization is restructuring the problem itself.
  Don't just optimize existing approach; consider different approaches.
language: language-agnostic
category: optimization
rule_id: CHANGE-PROBLEM
priority: warn
tags:
- algorithmic
- restructuring
- big-picture
---
Often the best optimization is restructuring the problem itself.
Don't just optimize existing approach; consider different approaches.

## Good

- // Instead of: iterate all entities checking visibility
// Do: spatial partitioning, check only nearby

## Bad

- // Micro-optimizing the slow iteration
