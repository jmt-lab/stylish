---
type: Styleguide Rule
description: |-
  Handle each error deliberately: deal with it, return it, or in exceptional
  cases log.Fatal or panic. Do not discard errors with _ unless the call is
  documented never to fail, and then add a comment saying why.
language: go
category: error_handling
rule_id: HANDLE-EVERY-ERROR
priority: error
tags:
- errors
- handling
- google-style
---
Handle each error deliberately: deal with it, return it, or in exceptional
cases log.Fatal or panic. Do not discard errors with _ unless the call is
documented never to fail, and then add a comment saying why.

## Good

- if err := f.Close(); err != nil {
    return fmt.Errorf("close %s: %w", name, err)
}
- n, _ := b.Write(p) // bytes.Buffer.Write never returns a non-nil error

## Bad

- _ = f.Close()
- json.Unmarshal(data, &v) // error silently ignored
