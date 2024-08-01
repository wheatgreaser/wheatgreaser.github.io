# dynamic memory management
so what the fuck is a dynamic memory?? static memory is for static and global variables, it gets allocated when the program runs and persists through the lifetime of the program. automatic memory allocation is for function parameters and local variables, memory gets allocated and dealllocated when you go out of the block of code. but the size is fixed for both of these things, so the fuc you do when you get a person's name? we can givee an arbitratary size like 25 characters, but what if his name is longer than that? you're fucked. ALSO, if you want to be a smartass and make the upper bound something like 10 million characters, the porotion of memory that we call the stack will overflow (visual studio only allocates like 1 mb to the stack). dynamic memory allocation occurs in the heap, which is quite hugeee (gigabytes on a modern computer) so we do not have to worry about this shit. 

if we do some thing like

```
int *ptr = new int; 
*ptr = 21;
```
the "new int" part basically gets an integer worth of memory from the OS and returns the memory address of the memory given to us. we can now store an integer worth of data on it. then we can dereference the pointer and store some value in that memory. SWEEEEET.

we can 'delete' the ptr after w euse it, which doesn't actually doesn't delete anything it just returns the memory being pointed back to the OS (back to the heap).

```
delete ptr;
ptr = nullptr;
```

when we delete a pointer it becomes a dangling pointer. a dangling pointer points to a deallocated memory. so DONT FUCKING ACCESS IT. also, apparently, deleting regular pointers (without dynamic memory allocation) leads to some very weird behavior. 

if the OS doesn't have memory to give to you (from the heap that is) it will throw you a bad_alloc error. we can do

```
int* value = new (std::nothrow) int;
```

to do error handling. this will assign a nullptr to the pointer if there's so no available memory.  

we can do some fucked up shit to cause a memory leak, where the access to the dynamically created memory is lost and that memeory was never deallocated. 

```
int x = 5;
int* ptr = new int;
ptr = &x;
```


