---
title: "数据压缩算法"
date: 2019-03-13T20:07:35+08:00
draft: false
tags: 
   - ALG
categories:
  - 技术
  - 归档
---

[TOC]

介绍经典的数据压缩算法

<!--more-->

![cover](https://gitee.com/gdhu/prvpic/raw/master/2019-03-13-006.jpg)


# Data Compression


## 例子 基因组学

genomic data : ATCGATCGATCG...

如果用字符表示的话，一个字符是8bit。但实际一个基因片段中只有四个字母出现。使用2个bit就能表示这四个字母。

空字符为 '\0', NUL

## RunLength算法思想

算法介绍：

>runs of data (that is, sequences in which the same data value occurs in many consecutive data elements) are stored as a single data value and count, rather than as the original run. 

https://en.wikipedia.org/wiki/Run-length_encoding

### 算法实现

![2019-03-13-005](https://gitee.com/gdhu/prvpic/raw/master/2019-03-13-005.jpg)

黑白图像素越高，压缩比例越高。

最早用于传播电视信号。

而图片压缩格式，例如JPEG，属于有损失的压缩。

https://en.wikipedia.org/wiki/JPEG

### 游程编码算法不明白的地方：

为什么要写一个重新计数0呢？

![2019-03-13-003](https://gitee.com/gdhu/prvpic/raw/master/2019-03-13-003.jpg)

```java
    public static void compress() { 
        char run = 0; 
        boolean old = false;
        while (!BinaryStdIn.isEmpty()) { 
            boolean b = BinaryStdIn.readBoolean();
            if (b != old) {
                BinaryStdOut.write(run, LG_R);
                run = 1;
                old = !old;
            }
            else { 
                if (run == R-1) { 
                    BinaryStdOut.write(run, LG_R);
                    run = 0;
                    BinaryStdOut.write(run, LG_R); // 为什么要计数0呢？
                }
                run++;
            } 
        } 
        BinaryStdOut.write(run, LG_R);
        BinaryStdOut.close();
    }
```

### 游程编码的问题

尽管游程编码算法很高效，但是在处理<font color="Darkorange">**文本压缩**</font>就没那么高效了。我们需要其他的算法。

![2019-03-13-007](https://gitee.com/gdhu/prvpic/raw/master/2019-03-13-007.jpg)

从图中可以看出 416 / 96 = 433% ，文件越压缩越大了。

## Huffman Compression

