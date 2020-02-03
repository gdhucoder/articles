---
title: "用十年时间自学编程"
date: 2019-02-17T21:26:41+08:00
draft: false
tags: 
   - BOOK
categories:
  - 技术
  - 归档
---

[TOC]

业余时间翻译经典的博文。

Teach yourself programming in ten years 

原文链接：[ten years](http://norvig.com/21-days.html)

<!--more-->

# Teach yourself programming in ten years 

用十年时间自学编程

为什么每个人都这么急功近利？

走进任意一个书店，你将会看到《24小时自学java》和类似的C，SQL，Ruby，算法等类的书籍，花上几天甚至几小时你就能掌握它们。使用亚马逊高级搜索：[title: teach, yourself, hours, since: 2000 ，你会发现有512本这样的书。前十种中，有九本是编程书籍，剩下的一本是关于记账的。将"teach yourself"替换成"learn"或者将"hours"替换成"days"。

结论要么是每个人都急着想学编程或者是编程要比学习其他东西简单。Felleisen 等人在他们著作《how to design programs》也承认这种趋势，他在书中说：糟糕的编程很容易，白痴都可以在21天内学会它，即使他们是傻瓜。Abtruse Goose漫画也有他们的看法。

让我们分析一下《24小时掌握C++》这样的书名是什么意思：

**自学**：24小时内，你没有时间写几个重要的程序，不能从你的成功或者失败中学习。你没有时间和有经验的程序员一起工作，也无法理解生活在C++环境的感受。简而言之，你没有足够的时间学到很多东西。书中谈到只能谈到肤浅的东西，而不是深刻的理解。正如亚历山大.波普所说，一知半解是危险的。

**C++**：在24小时中，你可能学习到一些C++的语法（如果你对其他编程语言有了解的话），但是你不能学到更多的关于语言使用方面的知识。总之，如果你是一个初级程序员，你可以学会写C++风格基础的程序，但是你无法了解到C++到底好在什么地方（有哪些不足）。这么说有什么意义呢？Alan Perlis曾说过，如果一种编程语言不能影响到你对编程的认识，那么它是不值得学习的。一种可能的观点是，你必须学一点C++（或者更可能像JavaScript或者Processing）因为你需要使用先用的工具进行交互以完成特定的任务。但是，那么你学习的就不是编程，而是完成一项任务。

**24小时内**：悲催的是，24小时远远不够，请看下面。

## Teach Yourself Programming in Ten Years

研究表明很多领域例如象棋，音乐创作，绘画，游泳等等都需要大概十年时间学习。关键在于**刻意练习**，刻意练习并不是简单的重复，而是一次一次的通过任务挑战自己，分析任务执行的成败原因和你的表现。重复重复，没有捷径。

Malcolm Gladwell提出一个观点10000小时天才理论。

## So You Want to be a Programmer

- 对编程感兴趣，你要足够感兴趣，才能肯花费10年或者10000小时。

- 编程：最好的学习方式是**通过做学习， learning by doing**。

> the most effective learning requires a well-defined task with an appropriate difficulty level for the particular individual, informative feedback, and opportunities for repetition and corrections of errors.

- 和其他程序员交流，阅读代码。这比任何书或者课程都有效。

- 如果你想的话，可以上4年大学。

> Computer science education cannot make anybody an expert programmer any more than studying brushes and pigment can make somebody an expert painter

- 和其他程序员一同工作。在某些项目上成为最好的程序员，在某些项目上成为最差的程序员。

当你是最牛的人时，尝试领导项目，鼓励他人。当你是最差的人时，从大师身上学习，学习他们不喜欢做什么（因为他们会让你做这些事情）。

- 在其他程序员之后开展项目。理解其他人写的程序。了解理解程序需要什么知识，当最初的程序员不在时，修复bug。考虑如何设计你的程序，是其他人在你之后更容易维护。

- 学习至少5-6们编程语言。包括关注类抽象的 java或者c++，函数式编程的 lisp ml haskell，语法抽象的 lisp，支持声明式规范的 Prolog C++ templates，支持并行的例如Clojure Go。

- 记住计算机科学这个词中有个"计算机"。知道多长时间执行一条指令。。。

- 参与语言标准化。

通过书籍你能学多少东西是不确定的。当我第一个孩子出生时，我读了所有关于"如何做"的数据，但是仍然感觉自己是个新手。30个月后，我第二个孩子出生后，我又回去看书了么？没有，我依靠我自己的经验，事实上比专家写的几千页的书都有用。

>Gusteau's critic, Anton Ego, says: "Not everyone can become a great artist, but a great artist can come from anywhere."

## 答案

Approximate timing for various operations on a typical PC:

execute typical instruction	1/1,000,000,000 sec = 1 nanosec

fetch from L1 cache memory	0.5 nanosec

branch misprediction	5 nanosec

fetch from L2 cache memory	7 nanosec

Mutex lock/unlock	25 nanosec

fetch from main memory	100 nanosec

send 2K bytes over 1Gbps network	20,000 nanosec

read 1MB sequentially from memory	250,000 nanosec

fetch from new disk location (seek)	8,000,000 nanosec

read 1MB sequentially from disk	20,000,000 nanosec

send packet US to Europe and back	150 milliseconds = 150,000,000 nanosec

## 附录：语言的选择

第一门语言：Python。

## 收获

"刻意练习"才能成为一名好的程序员。
关于如何刻意练习，待以后分析。



