---
type: Styleguide Rule
description: |-
  Single-line block comments should have spaces after /* and before */.
  Multi-line block comments should have newlines after /* and before */.
language: rust
category: comments
rule_id: BLOCK-COMMENT-FORMAT
priority: warn
tags:
- comments
- formatting
- official
---
Single-line block comments should have spaces after /* and before */.
Multi-line block comments should have newlines after /* and before */.

## Good

- /* single space */
- /*
 * Multi-line
 * comment
 */

## Bad

- /*no spaces*/
