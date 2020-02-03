---
title: "13 | 线性排序：如何根据年龄给100万用户数据排序？"
date: 2019-04-20T18:23:20+08:00
draft: false
tags: 
   - 算法
categories:
  - 技术
  - 归档
---

[TOC]

本篇介绍线性时间排序。

![2019-03-20-004](https://gitee.com/gdhu/prvpic/raw/master/2019-03-20-004.jpg)

<!--more-->

![cover](https://gitee.com/gdhu/prvpic/raw/master/2019-03-09-001.png)

前两节中，我们着重分析了集中常见排序算法的原理、时间复杂度、空间复杂度、稳定性等。今天介绍三种时间复杂度是O(n)的排序算法：桶排序，计数排序、基数排序。因为这些排序算法的时间复杂度是线性的，所以我们把这类排序算法叫做
<font color="green">**线性排序**</font>
(Linear sort)。之所以能到线性时间的复杂度，主要原因是，这三个算法是非基于比较的排序算法，都不涉及元素之间的比较操作。

# 线性时间排序

## 桶排序

![桶排序](https://gitee.com/gdhu/prvpic/raw/master/2019-03-09-002.png)

视频： https://www.youtube.com/watch?v=VuXbEb5ywrU

Wiki：
https://en.wikipedia.org/wiki/Bucket_sort

桶排序的的主要思想是将数组中的元素分配到桶中，然后分别对桶中的元素进行排序。

桶排序的步骤是：

1. 首先初始化 <font color="Darkorange">**空桶**</font>

2. 分配：变量原始数组，将每个对象分配到对应的桶中

3. 每个桶中的元素进行排序。通常使用插入排序insertion sort

4. <font color="Darkorange">**收集（gather)**</font>顺序访问每个桶，取出元素，放回到原始数组。

![2019-03-20-003](https://gitee.com/gdhu/prvpic/raw/master/2019-03-20-003.jpg)

如果需要排序的数据有n个，将它们均匀的划分到m个桶内，每个桶有k=n/m个元素。每个桶内使用快排，时间复杂度为$O(klogk)$。m个桶排序的时间复杂度就是$O(nlog(n/m))$ 。 当桶的个数接近数据个数n时，$log(n/m)$就是一个非常小的常量，这个时候桶排序的时间复杂度接近$O(n)$。



## 计数排序

[geeksforgeeks](https://www.geeksforgeeks.org/counting-sort/)

[Counting sort wiki](https://en.wikipedia.org/wiki/Counting_sort)

计数排序(counting sort)为什么叫计数排序呢？因为排序算法中使用了一个count数组，用于统计待排序数组中每个key出现的次数。

这个算法也在《算法4》的第五章String出现了。

适用场景：适用于数据范围不大的场景，如果数据范围要比要排序的数据n大太多，就不适合用计数排序了。

```java
  public static void sort(int[] a) {

    int N = a.length;

    int max = a[0];
    for (int i = 1; i < a.length; i++) {
      if (a[i] > max) {
        max = a[i];
      }
    }

    int[] count = new int[max + 1];

    // compute frequency
    for (int i = 0; i < N; i++) {
      count[a[i]]++;
    }

    // transform counts into indices
    for (int i = 1; i < count.length; i++) {
      count[i] += count[i - 1];
    }

    StdOut.println("count: " + Arrays.toString(count));

    int[] res = new int[N];

    // Build the output character array
    // To make it stable we are operating in reverse order

//    for (int i = 0; i < N; i++) { // unstable
//      count[a[i]]--;
//      res[count[a[i]]] = a[i];
//    }

    for (int i = N - 1; i >= 0; i--) {
      res[count[a[i]] - 1] = a[i];
      count[a[i]]--;
    }

    // copy back
    for (int i = 0; i < N; i++) {
      a[i] = res[i];
    }

    StdOut.println("sort: " + Arrays.toString(a));

  }
```

## 基数排序

如何给10万或者100万个手机号码进行排序？

>基数排序的方式可以采用LSD（Least significant digital）或MSD（Most significant digital），LSD的排序方式由键值的最右边开始，而MSD则相反，由键值的最左边开始。

基数排序的时间复杂度是O(N)

把数据按照
<font color="Darkorange">**位**</font>
排序。对于每一位使用线性排序算法。同时对于按位的排序应该是稳定的。

## 问题

如何给100万用户按照年龄排序呢？ 答案是使用桶排序。将用户按照年龄1到120放到120个桶中，然后顺序遍历这120个桶中的元素，就完成了对100万用户按照年龄排序了。

## 思考题

假设我们现在需要对 D，a，F，B，c，A，z 这个字符串进行排序，要求将其中所有小写字母都排在大写字母的前面，但小写字母内部和大写字母内部不要求有序。比如经过排序之后为 a，c，z，D，F，B，A，这个如何来实现呢？如果字符串中存储的不仅有大小写字母，还有数字。要将小写字母的放到前面，大写字母放在最后，数字放在中间，不用排序算法，又该怎么解决呢？


