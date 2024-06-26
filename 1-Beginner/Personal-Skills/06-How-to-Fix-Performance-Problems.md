# How to Fix Performance Problems
[//]: # (Version:1.0.0)
Most software projects can be made with relatively little effort 10 to 100 times faster than they are at the time they are first released. ==Under time-to-market pressure, it is both wise and effective to choose a solution that gets the job done simply and quickly, but less efficiently than some other solution. However, performance is a part of usability, and often it must eventually be considered more carefully.==

==The key to improving the performance of a very complicated system is to analyse it well enough to find the *bottlenecks*==, or places where most of the resources are consumed. There is not much sense in optimizing a function that accounts for only 1% of the computation time. ==As a rule of thumb you should think carefully before doing anything unless you think it is going to make the system or a significant part of it at least twice as fast. 💨== There is usually a way to do this. Consider the test and quality assurance effort that your change will require. Each change brings a test burden with it, so it is much better to have a few big changes.

> [!question] 💨 *at least* twice as fast
> seems like a tall order, no?

After you've made a two-fold improvement in something, you need to at least rethink and perhaps reanalyze to discover the next-most-expensive bottleneck in the system, and attack that to get another two-fold improvement.

Often, the bottlenecks in performance will be an example of counting cows by counting legs and dividing by four, instead of counting heads. ==For example, I've made errors such as failing to provide a relational database system with a proper index on a column I look up a lot, which probably made it at least 20 times slower. 💩== Other examples include doing unnecessary I/O in inner loops, leaving in debugging statements that are no longer needed, unnecessary memory allocation, ==and, in particular, inexpert use of libraries and other subsystems that are often poorly documented with respect to performance==. This kind of improvement is sometimes called *low-hanging fruit*, meaning that it can be easily picked to provide some benefit.

> [!note] 💩 database indices
> I feel like I might have done this as well. in mongo, so not relational, but still.

What do you do when you start to run out of low-hanging fruit? Well, you can reach higher, or chop the tree down. You can continue making small improvements or you can seriously redesign a system or a subsystem. (This is a great opportunity to use your skills as a good programmer, not only in the new design but also in convincing your boss that this is a good idea.) However, before you argue for the redesign of a subsystem, you should ask yourself whether or not your proposal will make it five to ten times better.

Next [How to Optimize Loops](07-How-to-Optimize-Loops.md)
