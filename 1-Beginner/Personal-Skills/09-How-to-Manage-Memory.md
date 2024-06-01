# How to Manage Memory
[//]: # (Version:1.0.0)
==Memory is a precious resource that you can't afford to run out of. You can ignore it for a while but eventually you will have to decide how to manage memory.==

Space that needs to persist beyond the scope of a single subroutine is often called *heap allocated*. ==A chunk of memory is useless, hence *garbage*, when nothing refers to it.== Depending on the system you use, you may have to explicitly deallocate memory yourself when it is about to become garbage. More often you may be able to use a system that provides a *garbage collector*. A garbage collector notices garbage and frees its space without any action required by the programmer. ==Garbage collection is wonderful: it lessens errors and increases code brevity and concision cheaply. Use it when you can.==

But even with garbage collection, you can fill up all memory with garbage. A classic mistake is to use a hash table as a cache and forget to remove the references in the hash table. Since the reference remains, the referent is non-collectable but useless. This is called a *memory leak*. You should look for and fix memory leaks early. ==If you have long running systems memory may never be exhausted in testing but will be exhausted by the user.==

The creation of new objects is moderately expensive on any system. Memory allocated directly in the local variables of a subroutine, however, is usually cheap because the policy for freeing it can be very simple. ==You should avoid unnecessary object creation. 💀==

> [!note] 💀 oops
> I think this is particularly worth noting down in my case because I tend to create more objects than my program really needs.

An important case occurs when you can define an upper bound on the number of objects you will need at one time. If these objects all take up the same amount of memory, you may be able to allocate a single block of memory, or a buffer, to hold them all. The objects you need can be allocated and released inside this buffer in a set rotation pattern, so it is sometimes called a ring buffer. This is usually faster than heap allocation.

Sometimes you have to explicitly free allocated space so it can be reallocated rather than rely on garbage collection. Then you must apply careful intelligence to each chunk of allocated memory and design a way for it to be deallocated at the appropriate time. The method may differ for each kind of object you create. ==You must make sure that every execution of a memory allocating operation is matched by a memory deallocating operation eventually. 🐍== This is so difficult that programmers often simply implement a rudimentary form of garbage collection, such as reference counting, to do this for them.

> [!note] 🐍 excursus: memory management in python
> 
> in python, the statement "you must make sure that every execution of a memory allocating operation is matched by a memory deallocating operation eventually" is generally not applicable in the same way it is for languages like c or c++, where manual memory management is required. 
> 
> python uses automatic memory management with a built-in garbage collector, which handles the allocation and deallocation of memory. here’s how it works:
> 
> 1. **reference counting**: python primarily uses reference counting to keep track of the number of references to each object in memory. when an object's reference count drops to zero, meaning no references to the object exist, the memory occupied by the object is deallocated automatically.
> 
> 2. **garbage collection**: in addition to reference counting, python includes a garbage collector to detect and clean up reference cycles (i.e., groups of objects that reference each other but are no longer reachable from any other part of the program).
> 
> because of this automatic memory management, python programmers typically do not need to manually match memory allocation with deallocation. the garbage collector takes care of freeing up memory when it is no longer in use.
> 
> however, there are still some considerations to keep in mind:
> 
> - **resource management**: for non-memory resources like file handles, network connections, and database connections, you should manage resource allocation and deallocation explicitly. this can be done using context managers (`with` statement) to ensure proper acquisition and release of resources.
> 
> ```python
>   with open('file.txt', 'r') as file:
>       data = file.read()
>   # File is automatically closed here
> ```
> 
> - **memory leaks**: although python handles memory management automatically, you can still encounter memory leaks if you maintain references to objects that are no longer needed. this can prevent the garbage collector from deallocating memory.
> 
> - **circular references**: while python's garbage collector can handle circular references, they can delay the deallocation of objects. it's a good practice to break reference cycles if possible.
> 
> in summary, python's garbage collector does take care of most memory allocation and deallocation, so the strict matching of allocation and deallocation operations as described in the book is not necessary in python. however, you should still be mindful of resource management and potential memory leaks.

Next [How to Deal with Intermittent Bugs](10-How-to-Deal-with-Intermittent-Bugs.md)
