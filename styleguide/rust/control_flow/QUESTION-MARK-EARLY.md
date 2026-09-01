---
type: Styleguide Rule
description: |-
  The ? operator implements early return pattern cleanly. Use it to
  propagate errors up the call stack and keep happy path linear.
  More readable than manual match/if-let chains for error propagation.
language: rust
category: control_flow
rule_id: QUESTION-MARK-EARLY
priority: warn
tags:
- control-flow
- errors
- readability
- propagation
---
The ? operator implements early return pattern cleanly. Use it to
propagate errors up the call stack and keep happy path linear.
More readable than manual match/if-let chains for error propagation.

## Good

- fn load() -> Result<Data, Error> {
    let file = open_file()?;
    let content = read_file(file)?;
    parse(content)
}
- fn load_game() -> Result<GameState, Error> {
    let save = load_save()?;
    let level = load_level(&save.level)?;
    Ok(GameState::new(save, level))
}

## Bad

- fn load() -> Result<Data, Error> {
    match open_file() {
        Ok(file) => match read_file(file) { ... }
    }
}
- fn load_game() -> Result<GameState, Error> {
    match load_save() {
        Ok(save) => match load_level(&save.level) {...}
    }
}
