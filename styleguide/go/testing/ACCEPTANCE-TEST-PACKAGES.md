---
type: Styleguide Rule
description: |-
  To let users validate their own implementations of your interfaces, provide
  a footest package with functions that exercise an implementation and return
  descriptive errors, like fstest.TestFS. Call t.Fatal there only for setup
  failures.
language: go
category: testing
rule_id: ACCEPTANCE-TEST-PACKAGES
priority: hint
tags:
- testing
- acceptance
- interfaces
- google-style
---
To let users validate their own implementations of your interfaces, provide
a footest package with functions that exercise an implementation and return
descriptive errors, like fstest.TestFS. Call t.Fatal there only for setup
failures.

## Good

- // ExercisePlayer returns a nil error if p makes a correct move on b.
func ExercisePlayer(b *chess.Board, p chess.Player) error

if err := chesstest.ExercisePlayer(board, player); err != nil {
    t.Errorf("player failed acceptance test: %v", err)
}

## Bad

- func ExercisePlayer(t *testing.T, b *chess.Board, p chess.Player) {
    t.Fatal("bad move") // assertion-style; caller loses control
}
