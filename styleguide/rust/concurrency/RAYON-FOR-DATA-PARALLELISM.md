---
type: Styleguide Rule
description: |-
  For CPU-bound work over a collection, use rayon's par_iter instead of
  spawning threads by hand or running the work on an async runtime.
  Measure first: parallelism only pays off when each element does enough
  work.
language: rust
category: concurrency
rule_id: RAYON-FOR-DATA-PARALLELISM
priority: info
tags:
- concurrency
- parallelism
- rayon
- performance
- rust-skills
---
For CPU-bound work over a collection, use rayon's par_iter instead of
spawning threads by hand or running the work on an async runtime.
Measure first: parallelism only pays off when each element does enough
work.

## Good

- use rayon::prelude::*;

let thumbnails: Vec<Thumbnail> = images.par_iter().map(render_thumbnail).collect();

## Bad

- let handles: Vec<_> = images
    .chunks(images.len() / 8)
    .map(|chunk| {
        let chunk = chunk.to_vec();
        std::thread::spawn(move || chunk.iter().map(render_thumbnail).collect::<Vec<_>>())
    })
    .collect();
