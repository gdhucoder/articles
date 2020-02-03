---
title: "工业级的排序算法"
date: 2019-04-21T16:15:56+08:00
draft: false
tags: 
   - 算法
categories:
  - 技术
  - 归档
---

[TOC]

你所熟悉的语言中，排序算法是如何实现的？

<!--more-->

# 工业级的排序算法

java 1.7 中排序按照排序的内容可以分为基本类型和对象类型。

## java中排序的实现

### 基本数据类型


Arrays.sort()中

byte数组使用插入排序和计数排序(待排序数组元素个数大于29)结合。

short,char , int, long, float, double 小规模数组(元素个数46以下)使用插入排序，大规模数组使用双轴快排。long 小规模使用的quicksort

[dual-pivot-quicksort_geeksforgeeks](https://www.geeksforgeeks.org/dual-pivot-quicksort/)

### 对象类型


从源代码中看使用的是TimSort(为了兼容，保留到了归并排序)

```java
    public static void sort(Object[] a, int fromIndex, int toIndex) {
        rangeCheck(a.length, fromIndex, toIndex);
        if (LegacyMergeSort.userRequested)
            legacyMergeSort(a, fromIndex, toIndex);
        else
            ComparableTimSort.sort(a, fromIndex, toIndex, null, 0, 0);
    }
```

[TimSort](https://en.wikipedia.org/wiki/Timsort)

### Collections排序

Collections.sort()将集合转成数组进行排序。

```java
    default void sort(Comparator<? super E> c) {
        Object[] a = this.toArray();
        Arrays.sort(a, (Comparator) c);
        ListIterator<E> i = this.listIterator();
        for (Object e : a) {
            i.next();
            i.set((E) e);
        }
    }
```