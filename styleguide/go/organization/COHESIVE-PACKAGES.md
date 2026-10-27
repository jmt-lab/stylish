---
type: Styleguide Rule
description: |-
  Put tightly coupled types that clients use together in the same package;
  split off conceptually distinct pieces into small, focused packages. If
  users must import both packages to use either, merge them.
language: go
category: organization
rule_id: COHESIVE-PACKAGES
priority: info
tags:
- packages
- cohesion
- api
- google-style
---
Put tightly coupled types that clients use together in the same package;
split off conceptually distinct pieces into small, focused packages. If
users must import both packages to use either, merge them.

## Good

- // package http: client.go, server.go, cookie.go
- buf := bytes.Buffer{} // package name + type read as one identifier

## Bad

- // package request and package response, always imported together
- // one package holding the entire project
