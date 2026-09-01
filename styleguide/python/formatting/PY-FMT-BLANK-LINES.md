---
type: Styleguide Rule
description: Two blank lines between top-level definitions. One blank line between methods. Use blank lines sparingly within functions.
language: python
category: formatting
rule_id: PY-FMT-BLANK-LINES
priority: warn
tags:
- formatting
- readability
- pep8
---
Two blank lines between top-level definitions. One blank line between methods. Use blank lines sparingly within functions.

## Good

- def function1():
    pass


def function2():
    pass

- class MyClass:
    def method1(self):
        pass

    def method2(self):
        pass


## Bad

- def function1():
    pass
def function2():
    pass

