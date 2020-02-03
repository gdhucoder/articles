---
title: "The Bitter Lesson"
date: 2019-05-19T15:51:46+08:00	
draft: false
tags: 
   - 分享
categories:
  - 技术
  - 归档
---

[TOC]

分享[Sutton](https://en.wikipedia.org/wiki/Richard_S._Sutton)的一篇博客。


<!--more-->

# 痛苦的教训

![2019-05-19-001](https://gitee.com/gdhu/prvpic/raw/master/2019-05-19-001.jpg)

[the bitter lesson](http://www.incompleteideas.net/IncIdeas/BitterLesson.html)

今天又读了一遍Sutton的这篇博客。在这篇博客中，Sutton总结了AI研究的近几十年取得的进步的原因和教训。

文章中称AI取得显著的进步靠的不是依赖人的领域知识（例如象棋、围棋、语音识别），而是靠算力、搜索和学习（Search and Learning）。试图将人的领域知识解决问题短期内会取得一定效果，但长期看，取得长足进步的方法是不依赖于领域知识的。例如语音识别，一帮语言学家搞了几十年都没什么效果，离实用还差的很远，在[贾里尼克](https://baike.baidu.com/item/%E8%B4%BE%E9%87%8C%E5%B0%BC%E5%85%8B)提出了基于统计的语音识别方法后，语音识别才有了实用的可能。

Sutton说：

>we should build in only the meta-methods that can find and capture this arbitrary complexity. Essential to these methods is that they can find good approximations, but the search for them should be by our methods, not by us. We want AI agents that can discover like we can, not which contain what we have discovered. Building in our discoveries only makes it harder to see how the discovering process can be done.



下面这篇文章中提到了 episodic-meta RL 接下来可以看看：

[Reinforcement Learning, Fast and Slow](https://www.cell.com/trends/cognitive-sciences/fulltext/S1364-6613(19)30061-0)