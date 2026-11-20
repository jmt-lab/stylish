---
type: Styleguide Rule
description: |-
  Wrap files, sockets, and other Read or Write handles in BufReader or
  BufWriter when you do many small reads or writes, and lock stdout once
  for bulk output. Each unbuffered call is a syscall. Flush a BufWriter
  explicitly so write errors are not lost on drop.
language: rust
category: optimization
rule_id: BUFFERED-IO
priority: warn
tags:
- optimization
- io
- performance
- rust-skills
---
Wrap files, sockets, and other Read or Write handles in BufReader or
BufWriter when you do many small reads or writes, and lock stdout once
for bulk output. Each unbuffered call is a syscall. Flush a BufWriter
explicitly so write errors are not lost on drop.

## Good

- let mut output = BufWriter::new(File::create(path).context(CreateSnafu { path })?);
for record in records {
    writeln!(output, "{record}").context(WriteSnafu { path })?;
}
output.flush().context(WriteSnafu { path })?;

## Bad

- let mut output = File::create(path).context(CreateSnafu { path })?;
for record in records {
    writeln!(output, "{record}").context(WriteSnafu { path })?; // one syscall per line
}
