---
type: Styleguide Rule
description: |-
  Constructors cannot be async. Use static factory methods or init()
  patterns for async initialization.
language: typescript
category: async
rule_id: NO-ASYNC-CONSTRUCTORS
priority: error
tags:
- async
- initialization
- patterns
---
Constructors cannot be async. Use static factory methods or init()
patterns for async initialization.

## Good

- static async create(): Promise<MyClass> {
  const instance = new MyClass();
  await instance.init();
  return instance;
}
- async init() {
  this.data = await loadData();
}

## Bad

- constructor() {
  this.data = await loadData(); // Cannot await in constructor
}
