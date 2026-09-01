---
type: Styleguide Rule
description: |-
  Don't add features, flexibility, or abstractions for hypothetical
  future needs. Build what's needed now, refactor when needs change.
  You can prematurely optimize maintainability, flexibility, security,
  and robustness just like you can performance. Don't add abstractions
  or over-engineer 'in case' — add complexity only when justified by
  current, proven requirements.
language: language-agnostic
category: abstraction
rule_id: YAGNI
priority: warn
tags:
- yagni
- simplicity
- future-proofing
- premature-optimization
- flexibility
- complexity
- abstraction
---
Don't add features, flexibility, or abstractions for hypothetical
future needs. Build what's needed now, refactor when needs change.
You can prematurely optimize maintainability, flexibility, security,
and robustness just like you can performance. Don't add abstractions
or over-engineer 'in case' — add complexity only when justified by
current, proven requirements.

## Good

- // Simple, meets current needs
struct Config { int width; int height; };
- // Simple, direct code
void Process(Entity* e) { e->x += 1; }
- // Simple, works
void LoadConfig(const char* path)

## Bad

- // Over-engineered for 'maybe someday'
class Config {
    PluginSystem plugins;
    EventBus events;
    ...
};
- // Over-engineered for hypothetical future
template<Policy, Traits> AbstractProcessor...
- // Over-flexible for no reason
ConfigLoader<FileSystem, Parser, Validator, Cache>()
