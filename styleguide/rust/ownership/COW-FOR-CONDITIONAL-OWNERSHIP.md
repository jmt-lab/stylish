---
type: Styleguide Rule
description: |-
  Return Cow<'_, str> (or Cow<'_, [T]>) from a function that usually
  passes its input through unchanged but sometimes must allocate a
  modified copy. Callers then pay for an allocation only when one happens.
language: rust
category: ownership
rule_id: COW-FOR-CONDITIONAL-OWNERSHIP
priority: info
tags:
- ownership
- cow
- allocation
- rust-skills
---
Return Cow<'_, str> (or Cow<'_, [T]>) from a function that usually
passes its input through unchanged but sometimes must allocate a
modified copy. Callers then pay for an allocation only when one happens.

## Good

- fn escape_html(input: &str) -> Cow<'_, str> {
    if !input.contains(['<', '>', '&']) {
        return Cow::Borrowed(input);
    }
    Cow::Owned(input.replace('&', "&amp;").replace('<', "&lt;").replace('>', "&gt;"))
}

## Bad

- fn escape_html(input: &str) -> String {
    input.replace('&', "&amp;").replace('<', "&lt;").replace('>', "&gt;") // allocates every time
}
