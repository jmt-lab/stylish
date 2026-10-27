---
type: Styleguide Rule
description: |-
  At FFI boundaries: use #[repr(C)] for shared structs, sized integer types,
  CString / CStr for strings, allocate and free on the same side, wrap
  foreign-owned pointers in an RAII type whose Drop frees them, check for null
  and return Result, and never let a panic unwind across extern "C".
language: rust
category: safety
rule_id: FFI-SAFE-BOUNDARY
priority: error
tags:
- safety
- ffi
- unsafe
- beautiful-rust
---
At FFI boundaries: use #[repr(C)] for shared structs, sized integer types,
CString / CStr for strings, allocate and free on the same side, wrap
foreign-owned pointers in an RAII type whose Drop frees them, check for null
and return Result, and never let a panic unwind across extern "C".

## Good

- pub struct Handle(NonNull<ffi::handle_t>);

impl Handle {
    pub fn open(name: &str) -> Result<Self, OpenError> {
        let name = CString::new(name).context(InteriorNulSnafu)?;
        // SAFETY: `name` is a valid NUL-terminated string for the call's duration.
        let raw = unsafe { ffi::handle_open(name.as_ptr()) };
        NonNull::new(raw).map(Self).context(OpenFailedSnafu)
    }
}

impl Drop for Handle {
    // SAFETY: the pointer came from handle_open and is freed exactly once.
    fn drop(&mut self) { unsafe { ffi::handle_close(self.0.as_ptr()) } }
}

## Bad

- pub fn open(name: &str) -> *mut ffi::handle_t {
    unsafe { ffi::handle_open(name.as_ptr() as *const c_char) } // not NUL-terminated, unchecked, leaks
}
