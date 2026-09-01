---
type: Styleguide Rule
description: "Acronyms should follow the same casing rules as words. Only capitalize \nthe first letter in camelCase/PascalCase contexts."
language: typescript
category: naming
rule_id: TS-ACRONYM-CASE
priority: info
tags:
- acronyms
- conventions
- readability
---
Acronyms should follow the same casing rules as words. Only capitalize 
the first letter in camelCase/PascalCase contexts.

## Good

- class HttpClient {} // Http not HTTP
- const apiUrl = 'https://...'; // api not API
- function parseXml() {} // Xml not XML

## Bad

- class HTTPClient {} // All caps breaks flow
- const APIUrl = '...'; // Inconsistent
- function parseXML() {} // All caps
