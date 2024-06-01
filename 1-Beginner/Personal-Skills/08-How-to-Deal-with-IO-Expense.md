# How to Deal with I/O Expense
[//]: # (Version:1.0.0)
For a lot of problems, processors are fast compared to the cost of communicating with a hardware device. This cost is usually abbreviated I/O, and can include network cost, disk I/O, database queries, file I/O, and other use of some hardware not very close to the processor. Therefore ==building a fast system is often more a question of improving I/O than improving the code in some tight loop, or even improving an algorithm.==

There are two very fundamental techniques to improving I/O: caching and representation. Caching is avoiding I/O (generally avoiding the reading of some abstract value) by storing a copy of that value locally so no I/O is performed to get the value. ==The first key to caching is to make it crystal clear which data is the master and which are copies.== There is only one master - period. ==Caching brings with it the danger that the copy sometimes can't reflect changes to the master instantaneously. 👉==

> [!example] 👉 copy reference (deep copy) vs. copy value (shallow copy)
> a code example showing a change in a copy reflecting a change in the master
> ```python
> # defining b as a deep copy of a, i.e., b and a will both point to the same list object, so a change in b will mean the same change in a
> a = [4, 7, 8, 3]
> b = a
> b.extend([323, 534, 996])
> b  # output: [4, 7, 8, 3, 323, 534, 996]
> a  # output: [4, 7, 8, 3, 323, 534, 996]
> 
> # defining b as a shallow copy of a, i.e., just the value of a is assigned to b; the two variables point to two distinct list objects
> a = [4, 7, 8, 3]
> b = a.copy()
> b.extend([323, 534, 996])
> b  # output: [4, 7, 8, 3, 323, 534, 996]
> a  # output: [4, 7, 8, 3]
> ```

Representation is the approach of making I/O cheaper by representing data more efficiently. This is often in tension with other demands, like human readability and portability.

Representations can often be improved by a factor of two or three from their first implementation. Techniques for doing this include using a binary representation instead of one that is human readable, transmitting a dictionary of symbols along with the data so that long symbols don't have to be encoded, and, at the extreme, things like ==Huffman encoding 🧬==.

> [!note] 🧬 excursus
> [video](https://youtu.be/JsTptu56GM8) on huffman coding
> <iframe width="560" height="315" src="https://www.youtube.com/embed/JsTptu56GM8?si=rholZkri9_IayyLM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

A third technique that is sometimes possible is to improve the locality of reference by pushing the computation closer to the data. For instance, if you are reading some data from a database and computing something simple from it, such as a summation, try to get the database server to do it for you. This is highly dependent on the kind of system you're working with, but you should explore it.

> [!quote] ooh! smort!
> *"A third technique that is sometimes possible is to improve the locality of reference by pushing the computation closer to the data. For instance, if you are reading some data from a database and computing something simple from it, such as a summation, try to get the database server to do it for you."*

Next [How to Manage Memory](09-How-to-Manage-Memory.md)