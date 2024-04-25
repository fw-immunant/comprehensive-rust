# Calling Rust

Exporting Rust functions and types to C is easy:

_interoperability/rust/libanalyze/analyze.rs_

```rust,editable
{{#include rust/libanalyze/analyze.rs:analyze_numbers}}
```

_interoperability/rust/libanalyze/analyze.h_

```c
{{#include rust/libanalyze/analyze.h:analyze_numbers}}
```

_interoperability/rust/libanalyze/Makefile_

```makefile
{{#include rust/libanalyze/Makefile}}
```

We can now call this from a C binary:

_interoperability/rust/analyze/main.c_

```c
{{#include rust/analyze/main.c:main}}
```

_interoperability/rust/analyze/Makefile_

```makefile
{{#include rust/analyze/Makefile}}
```

Build and run the binary:

```shell
$ cd libanalyze; make; cd -
$ cd analyze; make
$ ./analyze
```

<details>

`#[no_mangle]` disables Rust's usual name mangling, so the exported symbol will
just be the name of the function. You can also use
`#[export_name = "some_name"]` to specify whatever name you want.

</details>
