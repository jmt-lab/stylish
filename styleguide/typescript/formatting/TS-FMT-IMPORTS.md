---
type: Styleguide Rule
description: |-
  Sort imports alphabetically within each group. Groups follow
  IMPORT-ORDERING (external packages, internal absolute paths, relative
  imports). See IMPORT-ORDERING in organization.yaml.
language: typescript
category: formatting
rule_id: TS-FMT-IMPORTS
priority: info
tags:
- imports
- organization
---
Sort imports alphabetically within each group. Groups follow
IMPORT-ORDERING (external packages, internal absolute paths, relative
imports). See IMPORT-ORDERING in organization.yaml.

## Good

- import { a } from 'module-a';
import { b } from 'module-b';
import { c } from 'module-c';


## Bad

- import { c } from 'module-c';
import { a } from 'module-a';
import { b } from 'module-b';

