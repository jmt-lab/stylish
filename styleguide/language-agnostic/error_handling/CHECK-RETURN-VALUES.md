---
type: Styleguide Rule
description: |-
  Don't ignore return values from functions that can fail. Either check
  the return or explicitly document why it's safe to ignore.
language: language-agnostic
category: error_handling
rule_id: CHECK-RETURN-VALUES
priority: error
tags:
- errors
- safety
- correctness
---
Don't ignore return values from functions that can fail. Either check
the return or explicitly document why it's safe to ignore.

## Good

- if (!Connect(addr)) {
    HandleError();
}
- (void)Write(data); // Explicitly ignoring, documented why

## Bad

- Connect(addr); // Ignoring potential failure
