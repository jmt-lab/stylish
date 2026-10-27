---
type: Styleguide Rule
description: |-
  Document significant sentinel errors and error types a function returns,
  including whether the type is a pointer, so callers can use errors.Is and
  errors.As. Put package-wide error conventions in the package comment.
language: go
category: comments
rule_id: DOCUMENT-ERROR-RETURNS
priority: info
tags:
- documentation
- errors
- google-style
---
Document significant sentinel errors and error types a function returns,
including whether the type is a pointer, so callers can use errors.Is and
errors.As. Put package-wide error conventions in the package comment.

## Good

- // Read reads up to len(b) bytes from the File.
//
// At end of file, Read returns 0, io.EOF.
func (*File) Read(b []byte) (n int, err error)
- // If there is an error, it will be of type *PathError.
func Chdir(dir string) error

## Bad

- // Chdir changes the current working directory.
func Chdir(dir string) error // callers cannot know to errors.As(*PathError)
- // If there is an error, it will be of type PathError. (actually returns *PathError)
