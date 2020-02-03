---
title: "MarkDown内嵌标签"
date: 2019-03-02T19:26:09+08:00
draft: false
tags: 
   - Markdown
categories:
  - 技术
  - 归档
---

[TOC]

 关于Markdown支持html标签

<!--more-->

markdown支持和内联html，遇到特殊的样式可以直接写原生的html。

例如改变字体颜色：

<font face="黑体">我是黑体字</font>

```
<font face="黑体">我是黑体字</font>
```



<font color="DarkGreen">我喜欢使用darkgreen </font>

在sublime中使用，我们可以定义一个snippet，快捷键为tg+tab。

```
<snippet>
	<content><![CDATA[
<font color="green">**${1:input text}**</font>
]]></content>
	<!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
	<tabTrigger>tg</tabTrigger>
	<!-- Optional: Set a scope to limit where the snippet will trigger -->
	<!-- <scope>source.python</scope> -->
</snippet>
```