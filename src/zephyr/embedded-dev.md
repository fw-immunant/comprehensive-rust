# Embedded Dev: Working without luxuries

In embedded or kernel contexts we often don't have access to the niceties of userspace programming: normal I/O capabilities, or functionality that might block or in practice be reentrant if used in the kernel, such as concurrency or allocators.
