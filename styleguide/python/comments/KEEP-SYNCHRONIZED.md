---
type: Styleguide Rule
description: Update docstrings and comments when code changes. Stale comments mislead readers and are worse than no comments.
language: python
category: comments
rule_id: KEEP-SYNCHRONIZED
priority: error
tags:
- maintenance
- accuracy
- hygiene
---
Update docstrings and comments when code changes. Stale comments mislead readers and are worse than no comments.

## Bad

- def get_user(id):
    """Returns user name."""
    return User.objects.get(id=id)  # Returns User object, not name
