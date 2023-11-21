## Templated pool allocator
I wrote this allocator a few years back and it hasnt failed me yet. Its nothing special, it just allocates pools of memory and pulls objects from the pool.
This approach reduces the need to keep asking the operating system for more memory and reduces fragmentation as the memory is allocated in larger blocks.


<br><br/>
### Using the allocator

> You can pull objects from the pool using the 'Create()' function and return them with 'Destroy()'.

> Note that the constructor and destructor are called internally.
```c++
PoolAllocator<T> pool();

// Create and return a pointer to an object in the pool.
T* newObject = pool.Create();

// Free the pointer to the object from the pool.
pool.Destroy(newObject);

```

<br><br/>
### Custom allocator

> You can specify the parameters of the allocator by giving the allocator constructor a custom allocator struct.

> Note that sending in a custom allocator is optional. The default is to allocate a single pool of 24 objects.
```c++
CustomAllocator customAlloc;

// Number of pools to pre-allocate
customAlloc.poolCount = 1;

// Number of objects per pool
customAlloc.poolSize = 24;

PoolAllocator<T> pool( customAlloc );
```
