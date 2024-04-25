# Fallible allocation

The standard library now contains [APIs that enable fallible allocation](https://doc.rust-lang.org/alloc/?search=try_reserve), but it's up to us to use them.

In addition to all the `_reserve` methods, note [`Vec::push_within_capacity`](https://doc.rust-lang.org/alloc/vec/struct.Vec.html#method.push_within_capacity).
