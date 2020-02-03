---
title: "算法4习题 2.1.12"
date: 2018-08-06T08:00:00+08:00
draft: false
tags: 
   - JAVA
categories:
  - 技术
  - 归档
---


# 算法4习题 2.1.12

## 问题
Instrument shellsort to print the number of compares divided by the array size for each increment. Write a test client that tests the hypothesis that this number is a small constant, by sorting arrays of random Double values, using array sizes that are increasing powers of 10, starting at 100.

打印希尔排序中每个增量带来的比较次数和数组大小的比值。
验证该值是一个小常数。

## 思路

统计每个增量对应的比较次数。
```java
  private static boolean less(Comparable v, Comparable w) {
    count ++ ;
    return v.compareTo(w) < 0;
  }
```

## 解答

Extensive experiments suggest that the average number of compares per increment might be N^(1/5)
大量实验表明每个增量的比较次数约为N的1/5次方。

这个结果，我觉得是有点怪的。题目中说是一个小常数，我理解是不变的常数。但是结果看下来，发现数值是变的。

```java
For array length =       1000, N^(1/5): 3.98 
h:        364 	       0.81 
h:        121 	       1.67 
h:         40 	       2.26 
h:         13 	       2.80 
h:          4 	       3.57 
h:          1 	       2.70 

For array length =      10000, N^(1/5): 6.31 
h:       9841 	       0.02 
h:       3280 	       0.90 
h:       1093 	       1.71 
h:        364 	       2.36 
h:        121 	       2.96 
h:         40 	       3.70 
h:         13 	       4.35 
h:          4 	       3.75 
h:          1 	       2.74 

For array length =     100000, N^(1/5): 10.00 
h:      88573 	       0.11 
h:      29524 	       0.98 
h:       9841 	       1.76 
h:       3280 	       2.40 
h:       1093 	       2.98 
h:        364 	       3.67 
h:        121 	       4.98 
h:         40 	       6.49 
h:         13 	       8.70 
h:          4 	       4.72 
h:          1 	       2.74 

For array length =    1000000, N^(1/5): 15.85 
h:     797161 	       0.20 
h:     265720 	       1.05 
h:      88573 	       1.83 
h:      29524 	       2.45 
h:       9841 	       3.07 
h:       3280 	       3.84 
h:       1093 	       5.00 
h:        364 	       6.48 
h:        121 	       8.78 
h:         40 	      13.68 
h:         13 	      10.22 
h:          4 	       4.85 
h:          1 	       2.75 
```
