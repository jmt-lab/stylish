---
type: Styleguide Rule
description: 'TODO comments must include username and context. Format: TODO(username): description. Link to issue tracker when applicable.'
language: python
category: comments
rule_id: TODO-FORMAT
priority: info
tags:
- todo
- maintenance
- tracking
---
TODO comments must include username and context. Format: TODO(username): description. Link to issue tracker when applicable.

## Good

- # TODO(carmack): Optimize with NumPy vectorization (issue #42)
- # TODO(jsmith): Remove after Python 3.9 EOL

## Bad

- # TODO: fix this
- # FIXME
