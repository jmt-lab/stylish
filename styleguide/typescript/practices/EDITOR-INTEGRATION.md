---
type: Styleguide Rule
description: |-
  ESLint and TypeScript should run in editor. See errors as you type,
  not after commit. Configure VS Code, WebStorm, etc.
language: typescript
category: practices
rule_id: EDITOR-INTEGRATION
priority: info
tags:
- editor
- feedback
- productivity
---
ESLint and TypeScript should run in editor. See errors as you type,
not after commit. Configure VS Code, WebStorm, etc.

## Good

- // .vscode/settings.json with eslint.enable: true

## Bad

- // No editor integration, errors found in CI
