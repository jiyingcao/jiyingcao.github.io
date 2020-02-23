---
title: 阅读AOSP源代码的正确姿势
date: 2019-06-16 12:36:40
tags:
- AOSP
---

> "Read the Fucking Source Code"
> — Linus Torvalds

“去读那XX的源代码”——Linus大神的至理名言，如雷贯耳，振聋发聩。

大神用语一向粗鄙。然而他足够伟大，伟大到粗鄙都成了他伟大的注脚。

普通人自然是没有资本粗鄙起来。当AOSP源码如山般横亘在面前时，我感觉自己化身成了愚公，手里只有一把铁锹。

好在有无数先行的愚公已经铲出了一条条羊肠小道——相比较我自己的愚鲁与懈怠，先行者们明明已经不是愚公，而是智叟了（此处褒义）。

源码该怎么读？对于AOSP这种太行王屋级别的工程，其入门之艰辛，远不是一句“万事开头难”就能形容的。云山雾罩，分分钟让人想起那套畅销书《从入门到放弃》（误）。

最务实的目标，反而是选择最容易的突破口，让自己不那么容易放弃。拿起铁锹，选择最平坦的羊肠小道，边走边挖。

对于大多数普通的Android程序员来说，对Java的掌握程度远远超过C/C++，对Android Studio的得心应手也远远凌驾于Source Insight之辈。我们从Java层开始，用Android Studio阅读。

# Hello, (Java) World!

AOPS运行的第一个Java程序是```Zygote```。熟悉Java的程序员，都知道Java程序从启动类的```main()```方法开始执行。我们只要从```Zygote```的启动类开始，从```main()```方法开始，就是阅读AOSP源码的入门姿势了。

# "Zygote"—受精卵

> "There are only two hard things in Computer Science: cache invalidation and naming things."
> — Phil Karlton

作为计算机领域两大难题之一，命名，往往能起到正向或者反向的效果。所幸AOSP源码里的命名还是比较明白易懂的，没有某些人写代码那么天马行空 : )

> **Zygote** is an Android system service that is the parent of all Android application processes.

维基百科说，Zygote是所有Android应用进程的父进程（parent）。

zygote不是一个常用的单词，它的意思是受精卵。生物的所有细胞，都是由受精卵分裂而来；Android世界的每一个进程，都是由```Zygote```进程创建而来，这就是它被命名为"Zygote"的原因吧。

现在，请记得```Zygote```的终极使命：创建所有Android应用进程。它的无数行源代码，可能让你头晕眼花，但一定要记得，所有的代码都是为了这个终极使命：创建Android应用进程。

# ZygoteInit.java—启动类

前面说了，```Zygote```是个Java程序，而Java程序的入口是某个类（启动类）的```main()```方法。对于```Zygote```来说，启动类是```ZygoteInit```，完整路径是frameworks/base/core/java/com/android/internal/os/ZygoteInit.java

记不住也没关系，这就是为什么要用趁手的工具，Android Studio。Ctrl+N，输入“ZygoteInit”，就能找到并打开了：