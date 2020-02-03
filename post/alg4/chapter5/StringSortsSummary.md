---
title: "String SortsSummary 字符串排序总结"
date: 2019-02-01T13:32:20+08:00
draft: false
tags: 
   - ALG
categories:
  - 技术
  - 归档
---

[TOC]

 整理字符串排序的知识点。

<!--more-->

# 字符排序 String Sorts

## Key-indexed counting 键索引计数法

![算法P1](https://gitee.com/gdhu/prvpic/raw/master/算法P1.png)

![算法P2](https://gitee.com/gdhu/prvpic/raw/master/算法P2.png)

![算法P3](https://gitee.com/gdhu/prvpic/raw/master/算法P3.png)


## LSD 低位优先字符串排序法

least-significant-digit first (LSD) string sort

比较适用于固定宽度的字符串排序，从右向左，对于每个位置上的字符调用key-indexed counting算法

时间复杂度O(NW)，忽略WR，线性级别

伪代码如下：

```java

public static void sort(String[] a, int W)
{
	int N = a.length;
	int R = 256;
	String[] aux = new String[N];

	for(int d=W-1; d>=0; d--)
	{
		int[] count = new int[R+1];
		for (int i=0; i<N; i++) {
			count[a[i].charAt(d)+1]++;
		}
		for (int r=0; r<R; r++) {
			count[r+1]+=count[r];
		}
		for (int i=0; i<N; i++) {
			aux[count[a[i].charAt(d)]++] = a[i];
		}
		for (int i=0; i<N; i++) {
			a[i] = aux[i];
		}
	}
}

```

## MSD




