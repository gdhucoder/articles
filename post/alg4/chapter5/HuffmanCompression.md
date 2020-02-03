---
title: "Huffman Compression"
date: 2019-04-03T16:25:34+08:00
draft: false
tags: 
   - ALG
categories:
  - 技术
  - 归档
---

[TOC]

总结霍夫曼压缩的相关重点。

<!--more-->

# Huffman Compression

![构建霍夫曼树的过程](https://gitee.com/gdhu/prvpic/raw/master/2019-04-03-001.jpg)

## 压缩

### 压缩的步骤如下：

读取输入

将输入中出现的每个char值的出现频率制成表格

根据频率构造相应的霍夫曼编码树

构造编译表，将输入中的每个char值和一个比特字符串相关联。

将单词查找树编码为比特字符串并写入输出流

将输入的字符总数做为比特字符串写入输出流

使用编译表将输入的每个字符写入到输出流

```java
例如：ABRACADABRA!

! : 1010
A : 0
B : 111
C : 1011
D : 100
R : 110

单词查找树编码       :01010000010010100010001001000011010000110101010010101000010
字符串长度12        :00000000000000000000000000001100
霍夫曼编码对应的输入 :01111100101101000111110010100


```

![2019-04-03-002](https://gitee.com/gdhu/prvpic/raw/master/2019-04-03-002.jpg)

## 展开

读取单词查找树（编码在比特流的开头）

读取需要解码的字符个数

使用单词查找树将比特流解码

## 特殊字符含义

```code
ASCII码的含义
\0 表示 NUL 字符串结束
10 表示 LF line feed 换行键
13 表示 CR  carriage return 回车键
```

Mac，以<CR>做为文本文件行尾的标识符

UNIX，以<LF>做为文本文件行尾的标识符

WINDOWS，以<CR><LF>为行尾的标志.

[百度百科ASCII](https://baike.baidu.com/item/ASCII/309296?fromtitle=ASCII%E7%BC%96%E7%A0%81&fromid=3712529)

