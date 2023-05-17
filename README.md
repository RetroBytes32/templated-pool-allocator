## Templated pool allocator
I wrote this allocator a few years back and it hasnt failed me yet. Its nothing special, it just allocates pools of memory and pulls objects from the pool.
This approch reduces the need to keep asking the operating system for more memory and reduces fragmentation as the memory is allocated in larger blocks.
