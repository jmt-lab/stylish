---
type: Styleguide Rule
description: |-
  Keep build.rs small, deterministic, and offline. Emit
  cargo::rerun-if-changed for every input so it doesn't rerun on every
  build, write only to OUT_DIR, and never download files or touch the
  source tree.
language: rust
category: cargo
rule_id: MINIMAL-BUILD-SCRIPTS
priority: warn
tags:
- cargo
- build-scripts
- reproducibility
- rust-skills
---
Keep build.rs small, deterministic, and offline. Emit
cargo::rerun-if-changed for every input so it doesn't rerun on every
build, write only to OUT_DIR, and never download files or touch the
source tree.

## Good

- fn main() {
    println!("cargo::rerun-if-changed=proto/service.proto");
    prost_build::compile_protos(&["proto/service.proto"], &["proto"])
        .expect("protobuf schema is checked in and valid");
}

## Bad

- fn main() {
    // reruns on every change to any file, needs network, edits src/
    let schema = reqwest::blocking::get(SCHEMA_URL).unwrap().text().unwrap();
    std::fs::write("src/generated.rs", generate(&schema)).unwrap();
}
