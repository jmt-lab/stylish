---
type: Styleguide Rule
description: |-
  Test Bevy systems in a headless App without DefaultPlugins, inserting
  needed resources and advancing Time manually for determinism. Add one smoke
  test that adds the whole plugin and calls app.update() twice, since query
  conflicts and missing resources only surface when systems first run.
language: rust
category: bevy
rule_id: BEVY-HEADLESS-APP-TESTS
priority: info
tags:
- bevy
- testing
- ecs
- beautiful-rust
---
Test Bevy systems in a headless App without DefaultPlugins, inserting
needed resources and advancing Time manually for determinism. Add one smoke
test that adds the whole plugin and calls app.update() twice, since query
conflicts and missing resources only surface when systems first run.

## Good

- #[test]
fn test_plugin_runs_two_frames() {
    let mut app = App::new();
    app.add_plugins((MinimalPlugins, CombatPlugin));
    app.update();
    app.update();
}

## Bad

- #[test]
fn test_apply_damage() {
    assert_eq!(compute_damage(10, 2), 8); // only pure helpers tested; the plugin panics on frame one
}
