---
type: Styleguide Rule
description: When working around bugs in libraries, Python versions, or platforms, document what the bug is and when it can be removed.
language: python
category: comments
rule_id: WORKAROUND-DOCUMENTATION
priority: error
tags:
- workarounds
- bugs
- maintenance
---
When working around bugs in libraries, Python versions, or platforms, document what the bug is and when it can be removed.

## Good

- # Workaround for requests 2.28.0 SSL verification bug
# Can be removed once we upgrade to 2.28.1+
- # Python 3.8 doesn't support := operator, use temp variable

## Bad

- # Hack
if weird_condition:
