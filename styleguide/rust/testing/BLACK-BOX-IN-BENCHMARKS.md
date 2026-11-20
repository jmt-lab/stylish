---
type: Styleguide Rule
description: |-
  Pass benchmark inputs and results through std::hint::black_box so the
  optimizer can't constant-fold the input or delete the work being
  measured. Use criterion (or divan) for statistically sound benchmarks
  instead of timing loops with Instant.
language: rust
category: testing
rule_id: BLACK-BOX-IN-BENCHMARKS
priority: warn
tags:
- testing
- benchmarks
- performance
- rust-skills
---
Pass benchmark inputs and results through std::hint::black_box so the
optimizer can't constant-fold the input or delete the work being
measured. Use criterion (or divan) for statistically sound benchmarks
instead of timing loops with Instant.

## Good

- fn bench_parse(criterion: &mut Criterion) {
    criterion.bench_function("parse_header", |bencher| {
        bencher.iter(|| parse_header(black_box(SAMPLE_HEADER)));
    });
}

## Bad

- let start = Instant::now();
for _ in 0..1_000 {
    parse_header(SAMPLE_HEADER); // result unused: may be optimized away
}
println!("{:?}", start.elapsed());
