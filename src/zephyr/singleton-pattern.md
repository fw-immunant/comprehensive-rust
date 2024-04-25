# Singleton pattern

svd2rust [implements](https://docs.rs/svd2rust/latest/svd2rust/#peripheral-api) a singleton pattern for access to devices.

In short, there is a single global resource that code anywhere can attempt to obtain.
In properly designed codebases this will only occur lexically once.

Then the singleton can be sliced and diced and portions of it will be passed down to the modules that should control them.

If multiple modules need to interact with a single hardware peripheral,
some multiplexing abstraction can be constructed,
e.g. using [Rc](https://doc.rust-lang.org/stable/std/rc/struct.Rc.html)
or [GhostCell](https://docs.rs/ghost-cell/latest/ghost_cell/).
