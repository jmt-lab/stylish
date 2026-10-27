---
type: Styleguide Rule
description: |-
  Libraries should not make clients rely on package-level state (mutable
  globals, global registries, service locators, callback lists, lazy singleton
  clients). Expose instance types that clients create and pass explicitly as
  dependencies.
language: go
category: practices
rule_id: AVOID-GLOBAL-STATE
priority: warn
tags:
- global-state
- dependency-injection
- testing
- google-style
---
Libraries should not make clients rely on package-level state (mutable
globals, global registries, service locators, callback lists, lazy singleton
clients). Expose instance types that clients create and pass explicitly as
dependencies.

## Good

- package sidecar

type Registry struct{ plugins map[string]*Plugin }

func New() *Registry { return &Registry{plugins: make(map[string]*Plugin)} }
func (r *Registry) Register(name string, p *Plugin) error

## Bad

- package sidecar

var registry = make(map[string]*Plugin)

func Register(name string, p *Plugin) error // shared by all clients; tests interfere
- var client pb.UserAdminServiceClient
func Client() pb.UserAdminServiceClient { if client == nil { client = dial() }; return client }
