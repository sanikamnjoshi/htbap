# How to Understand Performance Problems
[//]: # (Version:1.0.0)
Learning to understand the performance of a running system is unavoidable for the same reason that learning debugging is. ==Even if you understand perfectly precisely the cost of the code you write, your code will make calls into other software systems that you have little control over or visibility into.== However, in practice performance problems are a little different and a little easier than debugging in general.

Suppose that you or your customers consider a system or a subsystem to be too slow. Before you try to make it faster, you must build a mental model of why it is slow. To do this you can use a ==profiling tool 🔍== or a good log to figure out where the time or other resources are really being spent. There is a famous dictum that 90% of the time will be spent in 10% of the code. I would add to that the importance of input/output expense (I/O) to performance issues. Often most of the time is spent in I/O in one way or another. Finding the expensive I/O and the expensive 10% of the code is a good first step to building your mental model.

> [!definition] 🔍 profiling tool
> Code profiling tools allow you to analyze the performance of your code by measuring the time it takes your methods to run and the amount of CPU and memory they consume.

> [!quote] coding pareto
> *"There is a famous dictum that 90% of the time will be spent in 10% of the code. \[...\] Finding the expensive I/O and the expensive 10% of the code is a good first step to building your mental model."*

There are many dimensions to the performance of a computer system, and many resources consumed. The first resource to measure is *wall-clock time*, the total time that passes for the computation. Logging *wall-clock time* is particularly valuable because it can inform about unpredictable circumstances that arise in situations where other profiling is impractical. However, this may not always represent the whole picture. Sometimes something that takes a little longer but doesn't burn up so many processor seconds will be much better in the computing environment you actually have to deal with. Similarly, memory, network bandwidth, database or other server accesses may, in the end, be far more expensive than processor seconds.

Contention for shared resources that are synchronized can cause deadlock and starvation. Deadlock is the inability to proceed because of improper synchronization or resource demands. ==Starvation is the failure to schedule a component properly. 🍔== If it can be at all anticipated, it is best to have a way of measuring this contention from the start of your project. Even if this contention does not occur, it is very helpful to be able to assert that with confidence.

> [!note] 🍔 starvation
> basically what is happening on the core workers right now because of 20,000+ instances of a job all being enqueued at the same time. although the job explicitly has `max_parallel` set to 2 (so 2 jobs can run at the same time on a worker; that's 4 jobs on 2 workers), since the system seems to be designed to prioritise jobs based on the time at which they are enqueued, any jobs enqueued after these 20,000 will have to wait until these are all done running, i.e., they will starve.

Next [How to Fix Performance Problems](06-How-to-Fix-Performance-Problems.md)
