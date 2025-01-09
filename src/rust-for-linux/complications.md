# Complications and Conflicts

There are a number of subtleties and unresolved conflicts between the Rust paradigm and the kernel one.

Some of these will require additional research and development
before Rust for Linux is ready for the prime-time,
while others merely require some additional learning and attention
on behalf of aspiring Rust for Linux developers.

One consequence of the current state of affairs is that a nightly version of the Rust compiler
is required to build Rust for Linux.
This does not present a problem for development, but it does for distributions that want to ship
kernels using Rust while avoiding depending on a bleeding-edge compiler toolchain.
Being able to build the project with a stable compiler is a significant goal of the Rust for Linux project;
the issues blocking this are tracked specifically[^1].

We'll visit the most significant of these in the interest of being aware of challenges we may encounter
when trying to implement kernel functionality in Rust.

[^1]: https://github.com/rust-lang/rust-project-goals/issues/116
