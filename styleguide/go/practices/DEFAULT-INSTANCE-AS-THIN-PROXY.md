---
type: Styleguide Rule
description: |-
  If you offer a convenience package-level API, it must be a thin proxy over
  an instance API that clients can create independently (like http.Handle and
  http.DefaultServeMux), used only by binaries rather than libraries, with
  documented invariants and a way to reset it.
language: go
category: practices
rule_id: DEFAULT-INSTANCE-AS-THIN-PROXY
priority: info
tags:
- global-state
- api
- google-style
---
If you offer a convenience package-level API, it must be a thin proxy over
an instance API that clients can create independently (like http.Handle and
http.DefaultServeMux), used only by binaries rather than libraries, with
documented invariants and a way to reset it.

## Good

- var DefaultRegistry = New()

func Register(name string, p *Plugin) error { return DefaultRegistry.Register(name, p) }

## Bad

- func Register(name string, p *Plugin) error { registry[name] = p } // no instance API exists
