---
title: "哈希表(1)"
date: 2019-04-27T22:00:00+08:00
draft: false
tags: 
   - 算法
categories:
  - 技术
  - 归档
---

[TOC]

介绍哈希表（散列表）

<!--more-->

# 如何使用散列表实现word中的单词拼写错误提示？

可以使用单词查找树或者散列表。

# 如何估算将常用单词保存在电脑中所占用的空间？

![2019-04-27-003](https://gitee.com/gdhu/prvpic/raw/master/2019-04-27-003.jpg)

# Java中的HashMap和Hashtable什么区别


- Hashtable是线程安全的，HashMap不是。在非线程应用程序(non-threaded applications)中，非同步的对象要比同步的对象快。

- Hashtable不允许null键或者值。HashMap允许一个null key，和任意数量的null values。

- HashMap继承了集合类的Map接口，遍历是无序的。LinkedHashMap迭代时按插入顺序的。Hashtable想要按照顺序遍历就不容易实现。

- 对于线程安全的情况，使用ConcurrentHashMap或者Collections.synchronizedMap()

```java
// Collections
public static <K,V> Map<K,V> synchronizedMap(Map<K,V> m) {
    return new SynchronizedMap<>(m);
}
```

# 散列思想

散列表用的是数组支持按照下标随机访问数据的特性，所以散列表其实就是数组的一种扩展，由数组演化而来。可以说，没有数组，就没有散列表。

利用数组支持下标随机访问，时间复杂度是$O(1)$这个特性，可以快速实现查询。

<font color="green">**散列函数**</font>：将关键字Key映射成数组下标的方法。

<font color="green">**散列值**</font>：散列函数计算得到的值叫做散列值（Hash值，哈希值）

![2019-04-27-004](https://gitee.com/gdhu/prvpic/raw/master/2019-04-27-004.jpg)