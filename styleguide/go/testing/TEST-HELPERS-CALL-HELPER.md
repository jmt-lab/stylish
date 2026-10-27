---
type: Styleguide Rule
description: |-
  Test helpers (setup and cleanup) that take *testing.T should call t.Helper()
  and fail with t.Fatal and a descriptive message when setup fails, rather
  than returning errors to the test. Put t after any ctx parameter. Helpers
  that cannot fail should not take t.
language: go
category: testing
rule_id: TEST-HELPERS-CALL-HELPER
priority: warn
tags:
- testing
- helpers
- t-helper
- google-style
---
Test helpers (setup and cleanup) that take *testing.T should call t.Helper()
and fail with t.Fatal and a descriptive message when setup fails, rather
than returning errors to the test. Put t after any ctx parameter. Helpers
that cannot fail should not take t.

## Good

- func mustAddGameAssets(t *testing.T, dir string) {
    t.Helper()
    if err := os.WriteFile(filepath.Join(dir, "pak0.pak"), pak0, 0644); err != nil {
        t.Fatalf("Setup failed: could not write pak0 asset: %v", err)
    }
}
- func readTestFile(ctx context.Context, t *testing.T, path string) string

## Bad

- func addGameAssets(t *testing.T, dir string) error { // returns error; caller must check
    return os.WriteFile(filepath.Join(dir, "pak0.pak"), pak0, 0644)
}
- func setup(t *testing.T) { t.Fatal("x") } // missing t.Helper: wrong line reported
