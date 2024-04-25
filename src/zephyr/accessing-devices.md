# Embedded dev: Accessing devices

Much of embedded and kernel development has to do with accessing hardware, both control registers or I/O faculties of the CPU/SoC and peripherals.

We'll see the ways Rust can mimic the fully-unsafe register/MMIO access that a C kernel might perform, then several higher-level abstractions that are commonly used atop this low-level interface.
