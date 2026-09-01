---
type: Styleguide Rule
description: Target 80 characters, allow up to 100. Prettier default is 80.
language: typescript
category: formatting
rule_id: TS-FMT-LINE-WIDTH
priority: warn
tags:
- line-length
- readability
---
Target 80 characters, allow up to 100. Prettier default is 80.

## Good

- const result = shortFunction(arg1, arg2);
- const result = longFunction(
  argument1,
  argument2,
  argument3
);


## Bad

- const result = veryLongFunctionCallWithManyArgumentsThatExceedsOneHundredCharactersAndBecomesHardToRead(arg1, arg2, arg3, arg4, arg5);
