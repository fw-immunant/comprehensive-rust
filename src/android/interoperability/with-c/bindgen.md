# Using Bindgen

The [bindgen](https://rust-lang.github.io/rust-bindgen/introduction.html) tool
can auto-generate bindings from a C header file.

First create a small C library:

_interoperability/bindgen/libbirthday.h_:

```c
{{#include bindgen/libbirthday.h:card}}
```

_interoperability/bindgen/libbirthday.c_:

```c
{{#include bindgen/libbirthday.c:print_card}}
```

Add this to your `Makefile`:

_interoperability/bindgen/Makefile_:

```makefile
{{#include bindgen/Makefile:libbirthday}}
```

Create a wrapper header file for the library (not strictly needed in this
example):

_interoperability/bindgen/libbirthday_wrapper.h_:

```c
{{#include bindgen/libbirthday_wrapper.h:include}}
```

You can now auto-generate the bindings:

_interoperability/bindgen/Makefile_:

```makefile
{{#include bindgen/Makefile:libbirthday_bindgen}}
```

Finally, we can use the bindings in our Rust program:

_interoperability/bindgen/Makefile_:

```makefile
{{#include bindgen/Makefile:print_birthday_card}}
```

_interoperability/bindgen/main.rs_:

```rust,compile_fail
{{#include bindgen/main.rs:main}}
```

Build and run the binary:

```shell
$ make print_birthday_card
$ ./print_birthday_card
```

Finally, we can run auto-generated tests to ensure the bindings work:

_interoperability/bindgen/Makefile_:

```makefile
{{#include bindgen/Makefile:libbirthday_bindgen_test}}
```

```shell
$ make libbirthday_bindgen_test
$ ./libbirthday_bindgen_test
```
