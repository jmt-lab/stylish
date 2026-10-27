---
type: Styleguide Rule
description: |-
  Group related code into files focused enough that a maintainer can guess
  where something lives. Avoid files with many thousands of lines and swarms
  of tiny files; there is no one-type-per-file rule. A doc.go may hold long
  package docs.
language: go
category: organization
rule_id: FOCUSED-FILES
priority: hint
tags:
- files
- packages
- google-style
---
Group related code into files focused enough that a maintainer can guess
where something lives. Avoid files with many thousands of lines and swarms
of tiny files; there is no one-type-per-file rule. A doc.go may hold long
package docs.

## Good

- // csv: reader.go (decoding), writer.go (encoding)
- // doc.go: package comment + package clause only

## Bad

- // server.go: 9000 lines covering every concern
- // one file per type: user.go, userid.go, username.go, ...
