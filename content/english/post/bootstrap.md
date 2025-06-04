---
title: "Compiler bootstrapping: philosophical metaphors in technology"
date: 2025-06-04T21:46:43+08:00
lastmod: 2025-06-04T21:46:43+08:00
draft: true
keywords: [compiler, bootstrap, philosophy]
description: ""
tags: [compiler, bootstrap, philosophy]
categories: [technical musings]
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

## What is a compiler 
To understand what compiler bootstrapping is and how compilers bootstrap, it is important to first clarify the nature of a compiler. From a usage point of view, **a compiler is a programme that converts text (i.e. source code) into machine code or intermediate code that can be executed**.
There are two things to keep in mind: 1. A compiler inherently contains a set of rules that let it know how to "translate" source code; 2. A compiler is a programme, meaning that it is able to perform the "translation" process automatically.

Imagine if there were no compilers, or even if there were no more programmes in the world, would we be able to compile code? The answer is yes. The answer is yes, because we can translate source code into machine code according to predefined rules. This process does not necessarily depend on the programme, and can even be done with pen and paper, and then written into the computer one by one. So, a compiler is just a tool that translates the source code for us, except that it transforms the source code into a programme far more efficiently than a human can.

But it should be noted that the compiler is also a programme, and its acquisition also requires the step source code -> executable code. And this step is exactly what the compiler itself is doing. In other words, the compiler as a "**programme**" can be created using the compiler as a "**tool**". When a compiler is created as a programme, it naturally has the property of being a tool, which in turn can create new programmes.

## Compiler bootstrapping process 
Today, the vast majority of programs require a compiler to be created (although the possibility of human compilation does exist). Since a compiler also belongs to a program, it generally needs a compiler to compile itself. In general, a compiler for a particular X programming language is called bootstrap (or self-hosted) if it was written for that language (i.e., a compiler for a new X language was compiled with a compiler for X).

A typical compiler bootstrap process is as follows (assuming that a compiler for language Y already exists and a compiler for language X needs to be created):
1. Write the source code in Y and compile it with the Y compiler to get the primitive compiler X0 for X (this compiler supports only the core functionality, i.e., a subset of the X language);
2. switch to the X language for development and compile with the X0 compiler to generate a new compiler X1;
3. Iterate, verify the original functionality and add new functionality to get the final X compiler.

## Reflections on Bootstrap 
In my opinion, what actually exists in the computer world is not a programming language, but a compiler that is **familiar with specific compilation rules**. And it's this particular compilation rule that corresponds to the programming language we use, which is an abstraction.

So I personally think that compiler bootstrapping is really about designing a tool that conforms to a certain rule with a tool that conforms to the same rule; and "**the ability to bootstrap**" refers to the ability to recreate itself as a tool without relying on other tools.

Furthermore, compilers are not the only ones that can bootstrap; this concept can be seen in many other places. For example, the development of the Linux operating system began on the Minix operating system, and it wasn't until version 0.11 that Linux developers were able to do their own development entirely on the Linux system[^1]. A classic example of this outside the computer field is machine tools. Machine tools make parts, and these parts can be used in the making of many things, including making new machine tools. In this way machine tools can be iterated and get better and better. Of course, there is certainly more to actual manufacturing than just a machine tool, so perhaps the entire manufacturing industry can be viewed as bootstrapped.

[^1]: [Linux kernel - Wikipedia](https://en.wikipedia.org/wiki/Linux_kernel)

In the bootstrapping process, I think there are two particular points to be aware of: 1. Can bootstrapping guarantee that the functionality will be fully inherited? 2. Can bootstrapping add new functionality?

In fact, the first point is not completely guaranteed. It is possible to change the functionality of the next generation of tools, or even remove some features. Sometimes these changes are not even active, and some small changes can lead to inconsistencies in the behaviour of the tool before and after. However, it seems that we don't need the next generation of tools to inherit all the functionality of the previous generation, as long as they inherit the core functionality that we need, that might be enough.

For the second point, the facts tell us that this seems to be right. The development of human society is a continuous process of creating and improving new tools from old ones. But thinking on a philosophical level, will the new tools that emerge from the old ones always be stronger? In more technical terms, can a bootstrapping system enhance itself indefinitely without relying on external forces? As [Gödel's Incompleteness Theorem](https://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems) reveals: a system cannot fully justify itself within itself. Does this mean that any self-generating system is destined to have boundaries that cannot be breached? If we consider human society as a self-reproducing system, where are our boundaries?