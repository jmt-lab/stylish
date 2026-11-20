---
type: Styleguide Rule
description: |-
  Don't throw errors away with let _ =, .ok(), an empty Err arm, or if let
  Ok(..) with no else. Propagate with ?, handle the error, or log it. If
  ignoring it really is correct, say why in a comment next to the discard.
language: rust
category: error_handling
rule_id: NEVER-SILENTLY-DISCARD-ERRORS
priority: error
tags:
- errors
- correctness
- results
- rust-skills
---
Don't throw errors away with let _ =, .ok(), an empty Err arm, or if let
Ok(..) with no else. Propagate with ?, handle the error, or log it. If
ignoring it really is correct, say why in a comment next to the discard.

## Good

- cache.store(key, &value).context(StoreCacheSnafu { key })?;

- // Best effort: the temp file is in the OS temp dir and is reaped anyway.
if let Err(error) = fs::remove_file(&temp_path) {
    tracing::debug!(%error, path = %temp_path.display(), "could not remove temp file");
}

## Bad

- let _ = cache.store(key, &value);

- fs::remove_file(&temp_path).ok();

- match send(message) {
    Ok(()) => {}
    Err(_) => {} // the message is gone and nobody knows
}
