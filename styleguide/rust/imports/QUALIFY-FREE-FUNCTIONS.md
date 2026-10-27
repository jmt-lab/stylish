---
type: Styleguide Rule
description: |-
  Call top-level functions from other modules or crates through their
  module name (module::function()), importing the module rather than the
  function. Unqualified lowercase calls are then assumed to be local.
  Exceptions: functions with already-disambiguated names (e.g. from C++
  interop) and modules whose names are prone to collisions.
language: rust
category: imports
rule_id: QUALIFY-FREE-FUNCTIONS
priority: warn
tags:
- imports
- functions
- readability
- google-style
---
Call top-level functions from other modules or crates through their
module name (module::function()), importing the module rather than the
function. Unqualified lowercase calls are then assumed to be local.
Exceptions: functions with already-disambiguated names (e.g. from C++
interop) and modules whose names are prone to collisions.

## Good

- use std::mem;

let old = mem::replace(&mut slot, new_value);
- use std::fs;

let contents = fs::read_to_string(path)?;

## Bad

- use std::mem::replace;

let old = replace(&mut slot, new_value);
- use std::fs::read_to_string;

let contents = read_to_string(path)?;
