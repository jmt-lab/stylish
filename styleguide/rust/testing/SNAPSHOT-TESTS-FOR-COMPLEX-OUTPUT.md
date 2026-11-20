---
type: Styleguide Rule
description: |-
  Test large or structured output, such as rendered text, serialized
  documents, compiler diagnostics, and CLI output, with insta snapshots
  instead of hand-maintained string literals. Review snapshot changes like
  code with cargo insta review.
language: rust
category: testing
rule_id: SNAPSHOT-TESTS-FOR-COMPLEX-OUTPUT
priority: info
tags:
- testing
- snapshots
- insta
- rust-skills
---
Test large or structured output, such as rendered text, serialized
documents, compiler diagnostics, and CLI output, with insta snapshots
instead of hand-maintained string literals. Review snapshot changes like
code with cargo insta review.

## Good

- #[test]
fn test_render_report_formats_summary() {
    let report = render_report(&sample_results());
    insta::assert_snapshot!(report);
}

## Bad

- #[test]
fn test_render_report_formats_summary() {
    let report = render_report(&sample_results());
    assert_eq!(report, "Summary\n=======\npassed: 12\nfailed: 1\n..."); // 80 more lines
}
