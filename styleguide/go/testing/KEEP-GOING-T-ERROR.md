---
type: Styleguide Rule
description: |-
  Prefer t.Error so a test reports every failing check in one run. Use t.Fatal
  only when continuing would be meaningless (setup failure, unusable output).
  In table tests, use t.Fatal inside t.Run subtests, or t.Error plus continue
  without subtests.
language: go
category: testing
rule_id: KEEP-GOING-T-ERROR
priority: warn
tags:
- testing
- t-error
- t-fatal
- google-style
---
Prefer t.Error so a test reports every failing check in one run. Use t.Fatal
only when continuing would be meaningless (setup failure, unusable output).
In table tests, use t.Fatal inside t.Run subtests, or t.Error plus continue
without subtests.

## Good

- gotMean, gotVar, err := MyDistribution(input)
if err != nil {
    t.Fatalf("MyDistribution(%v) returned unexpected error: %v", input, err)
}
if gotMean != wantMean {
    t.Errorf("MyDistribution(%v) mean = %v, want %v", input, gotMean, wantMean)
}
if gotVar != wantVar {
    t.Errorf("MyDistribution(%v) variance = %v, want %v", input, gotVar, wantVar)
}

## Bad

- if gotMean != wantMean {
    t.Fatalf("mean = %v, want %v", gotMean, wantMean) // hides the variance check
}
