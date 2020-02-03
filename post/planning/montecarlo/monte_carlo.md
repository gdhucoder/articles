---
title: "什么是蒙特卡罗"
date: 2017-11-26T21:25:07+08:00
draft: false
tags: 
   - PLANNING
   - MC
categories:
  - 技术
  - 归档
---

[TOC]

乍一听“蒙特卡罗”这个词，完全不知所云，我感到很奇怪，一个搜索算法Monte Carlo Tree Search为什么叫蒙特卡罗。
于是，就有了下面的文字。

本篇文章主要介绍MonteCarlo方法的由来，及简单的一个应用-求π的值。
下篇将会介绍：什么是Monte Carlo Tree Search算法。

<!--more-->

### 蒙特卡罗方法概述

蒙特卡罗方法又称统计模拟法、随机抽样技术，是一种随机模拟方法，以概率和统计理论方法为基础的一种计算方法，是使用随机数（或更常见的伪随机数）来解决很多计算问题的方法。将所求解的问题同一定的概率模型相联系，用电子计算机实现统计模拟或抽样，以获得问题的近似解。为象征性地表明这一方法的概率统计特征，故借用赌城蒙特卡罗命名。 

让我们看看蒙特卡罗赌城。

![赌城夜景](http://upload-images.jianshu.io/upload_images/4800606-ca8ec6986883110e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

赌城的标志。

![Casino](http://upload-images.jianshu.io/upload_images/4800606-f3f9bed551a7d351.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

赌城内部非常豪华，金碧辉煌。

![赌城内部](http://upload-images.jianshu.io/upload_images/4800606-614b4a625407154d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 蒙特卡罗方法的提出

蒙特卡罗方法于20世纪40年代美国在第二次世界大战中研制原子弹的“曼哈顿计划”计划的成员S.M.乌拉姆和J.冯·诺伊曼首先提出。数学家冯·诺伊曼用驰名世界的赌城—摩纳哥的Monte Carlo—来命名这种方法，为它蒙上了一层神秘色彩。在这之前，蒙特卡罗方法就已经存在。1777年，法国Buffon提出用投针实验的方法求圆周率∏。这被认为是蒙特卡罗方法的起源。

### 例子：π的计算

如何用蒙特卡罗方法计算圆周率π。正方形内部有一个相切的圆，它们的面积之比是π/4。现在，在这个正方形内部，随机产生10000个点（即10000个坐标对 (x, y)），计算它们与中心点的距离，从而判断是否落在圆的内部。如果这些点均匀分布，那么圆内的点应该占到所有点的 π/4，因此将这个比值乘以4，就是π的值。

![图例1-1](http://upload-images.jianshu.io/upload_images/4800606-384999767a54a361.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图例1-2：圆面积/正方形面积](http://upload-images.jianshu.io/upload_images/4800606-f6b6fc7aa77736bc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

使用R语言模拟抽样10000次的结果，估计π结果如下：

![图例1-3：抽样计算结果](http://upload-images.jianshu.io/upload_images/4800606-4e9d1109abb2e9f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图例1-4：R代码](http://upload-images.jianshu.io/upload_images/4800606-dae258e365af2434.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图例1-5：抽检区间1-2000次后估计π的误差](http://upload-images.jianshu.io/upload_images/4800606-29c37454a4920f86.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

从上图我们可以看出，随着抽样次数的增加，估计的π值和真实值越来越接近。

### 结语

关于什么是蒙特卡罗就介绍到这里。抽样的思想已在各个领域产生深刻的影响。

### 参考资料

将部分参考资料列出如下，感谢前人的工作！

* [mbalib中的部分介绍](http://wiki.mbalib.com/wiki/%E8%92%99%E7%89%B9%E5%8D%A1%E7%BD%97%E6%96%B9%E6%B3%95) 

* [阮一峰的博客](http://www.ruanyifeng.com/blog/2015/07/monte-carlo-method.html)



