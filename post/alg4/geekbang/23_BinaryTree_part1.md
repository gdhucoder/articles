---
title: "二叉树(1)"
date: 2019-05-01T15:57:17+08:00
draft: false
tags: 
   - 算法
categories:
  - 技术
  - 归档
---

[TOC]

介绍二叉树基础。

<!--more-->

# 二叉树

二叉树（Binary Tree）

## 树

![2019-05-01-007](https://gitee.com/gdhu/prvpic/raw/master/2019-05-01-007.jpg)

## 概念

![2019-05-01-008](https://gitee.com/gdhu/prvpic/raw/master/2019-05-01-008.jpg)

## 满二叉树，完全二叉树

![2019-05-01-002](https://gitee.com/gdhu/prvpic/raw/master/2019-05-01-002.jpg)

## 存储方式

### 链表

![2019-05-01-003](https://gitee.com/gdhu/prvpic/raw/master/2019-05-01-003.jpg)

### 数组

![2019-05-01-005](https://gitee.com/gdhu/prvpic/raw/master/2019-05-01-005.jpg)

![2019-05-01-004](https://gitee.com/gdhu/prvpic/raw/master/2019-05-01-004.jpg)

## 遍历

![2019-05-01-006](https://gitee.com/gdhu/prvpic/raw/master/2019-05-01-006.jpg)

## 代码

```java
  /**
   * preorder
   */
  public static void preOrder(Node n) {
    if (n == null) {
      return;
    }
    StdOut.println(n);
    preOrder(n.left);
    preOrder(n.right);
  }

  /**
   * inorder
   */
  public static void inOrder(Node n) {
    if (n == null) {
      return;
    }
    inOrder(n.left);
    StdOut.println(n);
    inOrder(n.right);
  }

  /**
   * postorder
   */
  public static void postOrder(Node n) {
    if (n == null) {
      return;
    }
    postOrder(n.left);
    postOrder(n.right);
    StdOut.println(n);
  }
```