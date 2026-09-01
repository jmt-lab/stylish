---
type: Styleguide Rule
description: |-
  Never use 'from module import *' except in __init__.py for
  re-exporting. Makes dependencies implicit and pollutes namespace.
language: python
category: organization
rule_id: NO-WILDCARD-IMPORTS
priority: error
tags:
- imports
- namespace
- clarity
---
Never use 'from module import *' except in __init__.py for
re-exporting. Makes dependencies implicit and pollutes namespace.

## Good

- from typing import List, Dict, Optional

## Bad

- from typing import *
