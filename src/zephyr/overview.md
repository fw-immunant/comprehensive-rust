# Fitting it together: Zephyr and Rust

### Why might we want to use Rust in Zephyr?

See next slide. In short, compile-time memory safety can avoid hardware isolation overheads.

### What is the status of integating Rust into Zephyr?

Zephyr has an outstanding issue ([zephyr/65837](https://github.com/zephyrproject-rtos/zephyr/issues/65837)) about Rust support.

It would be nice to have an interface that looks something like this (from the issue):

```rust
#![no_std]

fn main() {
    let dt = zephyr::devicetree::take().unwrap();
    let led = dt.chosen.led0;

    loop {
        led.toggle().unwrap();
        zephyr::sys::sleep(1000);
    }
}
```

Some issues:
  - Devicetree support currently goes through C `#define`s, which are hard to access from Rust.
  - Driver interaction: at the very least, some glue code will be needed to expose existing Zephyr APIs to Rust.
  - Build system: CMake support for Rust

No general consensus, and the discussion here focuses more on userspace though it isn't userspace-exclusive.

### `std` support: Should Zephyr implement a port of libstd?

`std` mostly tries to provide an interace to "typical" Unix-like OSes.
Zephyr has some functionality that these do not (e.g. real-time guarantees) and lacks some functionality that Unix-like OSes do provide.
It probably isn't the most effective move to support libstd directly; most useful code lives in libcore or liballoc.