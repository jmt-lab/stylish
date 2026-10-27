---
type: Styleguide Rule
description: |-
  Use + for a few strings and fmt.Sprintf for formatted output (fmt.Fprintf
  when writing to an io.Writer). Use strings.Builder for piecemeal building in
  loops, and templates for complex output.
language: go
category: declarations
rule_id: STRING-CONCATENATION-CHOICE
priority: info
tags:
- strings
- performance
- google-style
---
Use + for a few strings and fmt.Sprintf for formatted output (fmt.Fprintf
when writing to an io.Writer). Use strings.Builder for piecemeal building in
loops, and templates for complex output.

## Good

- key := "projectid: " + p
- str := fmt.Sprintf("%s [%s:%d]-> %s", src, qos, mtu, dst)
- b := new(strings.Builder)
for i, d := range digits {
    fmt.Fprintf(b, "digit %d is %d\n", i, d)
}

## Bad

- s := src.String() + " [" + qos.String() + ":" + strconv.Itoa(mtu) + "]-> " + dst.String()
- var s string
for _, d := range digits { s += fmt.Sprint(d) } // quadratic
- io.WriteString(w, fmt.Sprintf("x=%d", x)) // use fmt.Fprintf(w, ...)
