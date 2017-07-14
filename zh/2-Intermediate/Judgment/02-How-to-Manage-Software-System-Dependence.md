# 如何管理软件系统依赖
[//]: # (Version:1.0.0)
现代软件系统趋向于依赖大量的非直接可控的组件。通过协同与重用，这增加了生产效率。然而，每个组件会带来一些问题：

- 你该如何修复组件中的 bug？
- 组件限制你使用特殊的硬件或软件系统了吗？
- 如果组件完全坏掉了，你该做什么？

某些程度上解耦组件，让它独立可以被移除，总是最好的。如果组件被证明完全不可用，你可能能够使用不同的组件，但你可能必须自己写一个组件。解耦不是可移植性，但这让移植变得简单，这大多数时候是好事。

拥有组件源代码可以把风险降到1/4.有了源代码，你可以更容易地评估它，调试它，找到避免踩坑的方法，并且使得修复更容易。如果你进行修复，你必须把修复的内容提交给组件的拥有者，并且让修改合并到官方发布版中，否则你将不适地必须维护一个非官方版本。

Next [如何判断软件是否太不成熟了](03-How-to-Decide-if-Software-is-Too-Immature.md)