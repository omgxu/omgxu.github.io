---
title: "编译器的自举：技术中的哲学隐喻"
date: 2025-06-04T19:18:49+08:00
lastmod: 2025-06-04T19:18:49+08:00
draft: true
keywords: [编译器, 自举, 哲学]
description: ""
tags: [编译器, 自举, 哲学]
categories: [技术思考]
author: "Jinhao Xu"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: true
postMetaInFooter: true
hiddenFromHomePage: false
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: false
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: false
  options: ""

sequenceDiagrams: 
  enable: false
  options: ""

---

<!--more-->

## 什么是编译器
要了解什么是编译器的自举以及编译器是如何自举的，首先要明确编译器的本质。从使用的角度来说，**编译器是一个把文本（即源代码）转换成能执行的机器代码或中间代码的程序**。
其中有两点要注意：1.编译器内在含有一套规则，让它知道如何“翻译”源代码；2.编译器是一个程序，意味着它能够自动执行“翻译”过程。

试想，假如没有编译器，甚至世界上不再有程序，我们能否编译代码呢？答案是肯定的。因为我们完全可以按照预定的规则，把源码翻译为机器码。这个过程并不一定依赖于程序，甚至用纸笔就可以做到，然后再一位一位写入计算机。所以，编译器只是帮我们翻译源码的一个工具，只不过它将源码转变为程序的效率远远高于人类。

但是需要注意，编译器也是程序，它的获得也是需要源码->可执行代码这一步的。而这一步，恰恰是编译器自身在做的事。也就是说，编译器这个“**程序**”的诞生，可以使用编译器这个“**工具**”。当编译器作为程序被创造出来后，它会天然地具有工具这一属性，进而可以创造新的程序。

## 编译器自举过程
如今，绝大多数程序的诞生都需要编译器（尽管确实存在人肉编译的可能性）。既然编译器也属于程序，那一般来说，它也需要一个编译器来编译自己。一般而言，如果某X编程语言的编译器是由该语言编写的（也就是说用X语言的编译器编译出了新的X语言的编译器），就称为自举（或者自托管）。

一个典型的编译器自举过程如下（假设已经有了Y语言编译器，需要创造X语言编译器）：
1. 用Y语言编写源代码并用Y编译器编译，得到适用于X语言的初代编译器X0（此编译器只支持核心功能，即X语言的子集）；
2. 转用X语言进行开发，并用X0编译器进行编译，生成新的编译器X1；
3. 不断迭代，验证原有功能并且添加新功能，得到最终的X语言编译器。

## 自举的思考
在我看来，计算机世界中实际存在的不是编程语言，而是**熟悉特定编译规则**的编译器。而这特定的编译规则，才对应于我们使用的编程语言，这是一个抽象的概念。

所以我个人认为，编译器自举其实就是用符合某种规则的工具设计出符合同样规则的工具；而“**自举能力**”指的是能不依赖其他工具，重新制造出自身这一工具。

此外，并不只有编译器可以自举，这个概念可以在其他很多地方看到。例如，Linux操作系统的开发一开始是在Minix操作系统上进行的，直到0.11版本，Linux开发者可以完全在Linux系统上进行自身的开发了[^1]。在计算机领域外，一个典型的例子是机床。机床可以制作零件，这些零件可以用于很多东西的制作，包括制作新的机床。这样机床就能不断迭代，并且越来越好。当然，实际的制造肯定不单单靠一台机床，或许可以把整个制造业看成自举的对象。

[^1]: [Linux kernel - Wikipedia](https://en.wikipedia.org/wiki/Linux_kernel)

在自举过程中，我觉得尤其需要注意的两点是：1.自举能否保证功能被完全继承？2.自举能否添加新的功能？

事实上，第一点并不能完全保证。因为我们完全可以改变下一代工具的功能，甚至删去一些特性。有时候这些改变甚至并不是主动进行的，一些小变化也会导致前后工具行为不一致。但是，我们似乎也不需要下一代工具完全继承上一代的功能，只要能继承我们需要的核心功能或许就够了。

对于第二点，事实告诉我们这似乎是对的。人类社会的发展，就是一个不断用旧工具创造、改进新工具的过程。但是从哲学层面思考，从旧工具中产生的新工具会一直更强吗？用更专业的话来说，一个自举系统是否可以在不依赖外部力量的前提下，无限增强自身能力？正如[哥德尔不完备定理](https://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems)所揭示的：一个系统无法在自身之中完全证明自己的正确性。这是否意味着，任何自我生成的体系，都注定存在无法突破的边界？倘若把人类社会作为一个自举的系统，我们的边界又在哪里呢？