---
type: Styleguide Rule
description: |-
  For C-style cleanup, using goto to a single cleanup label is clearer
  than duplicated cleanup code or complex error handling.
language: language-agnostic
category: control_flow
rule_id: GOTO-FOR-CLEANUP
priority: info
tags:
- goto
- cleanup
- error-handling
---
For C-style cleanup, using goto to a single cleanup label is clearer
than duplicated cleanup code or complex error handling.

## Good

- if (error) goto cleanup;
...
cleanup:
    Free(resources);
    return result;

## Bad

- if (error) { Free(r1); Free(r2); return; }
...
Free(r1); Free(r2); // Duplicated
