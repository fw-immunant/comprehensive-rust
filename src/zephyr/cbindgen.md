# Calling Rust with `cbindgen`

We can automatically generate a `.h` for accessing our Rust with the [`cbindgen`](https://github.com/mozilla/cbindgen) tool.

It can be used as a command-line tool or as a library from `build.rs` build scripts.

`cbindgen` is not the cleanest tool in the world (it has admittedly grown features ad-hoc),
but can eliminate the need to manually update headers when Rust code changes.
