# Integrating with an existing codebase

Zephyr won't be ported to Rust in a day. If we want to use Rust,
we'll be interoperating with a mostly-C codebase for the foreseeable future.

What does this look like?
Luckily, the Rust ecosystem has some well-tested tools for interoperability in both directions
(Rust calling C and vice versa).
