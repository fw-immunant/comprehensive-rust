# Isolation: Compile-time vs. Runtime

For isolating independent processes, we need to make guarantees that they do not access each other's resources in unintended ways.

Traditionally, operating systems have achieved this with hardware access control mechanisms.
These include memory protection (RWX flags in the page table), protection rings, and others.
They dynamically prevent accesses that should be forbidden based on a hardware notion of what should be allowed (page flags, current CPU privilege ring, etc.).
Hardware access control mechanisms often come with some performance cost,
but this is generally less than implementing the same checks in software without hardware support.

If software can be proven ahead of time to never perform these forbidden accesses, we don't need hardware or software implementations of dynamic checks.
If we can express our isolation needs in a way captured by Rust's compile-time memory safety guarantees, we can avoid the overhead of runtime isolation enforcement.
This overhead is even more worth avoiding on small/slow platforms.

