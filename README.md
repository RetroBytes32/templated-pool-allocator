## Templated pool allocator
I wrote this allocator a few years back and it hasnt failed me yet. Its nothing special, it just allocates pools of memory and pulls objects from the pool.
This approch reduces the need to keep asking the operating system for more memory and reduces fragmentation as the memory is allocated in larger blocks.


<br><br/>
### Custom allocator

> You can specify the parameters of the allocator by giving the allocator constructor a custom allocator.

> Note that sending in a custom allocator is optional. The default is one pool of 24 objects.
```c++
// Custom allocator
CustomAllocator customAlloc;

// Number of pools to pre-allocate
customAlloc.poolCount = 1;

// Number of objects per pool
customAlloc.poolSize = 24;
```

<br><br/>
### Using the allocator

> You can pull objects from the pool using the create/destroy functions.

> Note that the constructor and destructor are called internally.
```c++
PoolAllocator<T> pool( customAlloc );

T* newObject = pool.Create();
pool.Destroy(newObject);

```
