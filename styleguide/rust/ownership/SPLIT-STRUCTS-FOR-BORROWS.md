---
type: Styleguide Rule
description: |-
  When one large struct causes borrow conflicts across method calls, split
  it into smaller structs composed in the parent so disjoint parts can be
  borrowed independently. The compiler tracks disjoint field borrows within
  one function, but not across &mut self methods. Avoid self-referential
  structs.
language: rust
category: ownership
rule_id: SPLIT-STRUCTS-FOR-BORROWS
priority: info
tags:
- ownership
- borrowing
- design
- beautiful-rust
---
When one large struct causes borrow conflicts across method calls, split
it into smaller structs composed in the parent so disjoint parts can be
borrowed independently. The compiler tracks disjoint field borrows within
one function, but not across &mut self methods. Avoid self-referential
structs.

## Good

- struct Game { world: World, renderer: Renderer }

fn frame(game: &mut Game) {
    game.renderer.draw(&game.world); // disjoint field borrows
}

## Bad

- impl Game {
    fn frame(&mut self) {
        let world = self.world().clone(); // clone to dodge &mut self conflict
        self.draw(&world);
    }
}
