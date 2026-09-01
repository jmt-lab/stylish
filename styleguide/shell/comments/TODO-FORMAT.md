---
type: Styleguide Rule
description: 'TODO comments should include username and date: # TODO(username): Description'
language: shell
category: comments
rule_id: TODO-FORMAT
priority: info
tags:
- comments
- todo
---
TODO comments should include username and date: # TODO(username): Description

## Good

- # TODO(john): Add error handling for network failures

## Bad

- # TODO: fix this
- # FIXME later
