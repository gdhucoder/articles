---
title: "MarkDown Preview MathJax"
date: 2018-04-05T07:00:00+08:00
draft: false
tags: 
   - LATEX
   - MATHJAX
categories:
  - 技术
  - 归档
---

[TOC]

# 关于MarkDown中的公式

<!--more-->

## 显示LaTeX公式

例如我们要显示公式：

```
When \\( a \ne 0 \\), there are two solutions to \\(ax^2 + bx + c = 0\\) and they are:
$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$

$$
\begin{aligned}
\dot{x} & = \sigma(y-x) \\
\dot{y} & = \rho x - y - xz \\
\dot{z} & = -\beta z + xy
\end{aligned}
$$
$$
a = b +  C + d
$$
```

显示后的样子：

When \\( a \ne 0 \\), there are two solutions to \\(ax^2 + bx + c = 0\\) and they are:
$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$

$$
\begin{aligned}
\dot{x} & = \sigma(y-x) \\
\dot{y} & = \rho x - y - xz \\
\dot{z} & = -\beta z + xy
\end{aligned}
$$
$$
a = b +  C + d
$$



## MarkDownPad2 中显示公式 

可以选择在MarkDownPad2中设置：
Options->Advanced->HTML Header Edit->保存->F6

就可以在浏览器中显示公式了。但是有个问题：不能在LiveView中实时渲染公式。

```
<!--
<script src='C:\Users\x1c\Downloads\MathJax-master\MathJax-master\MathJax.js?config=TeX-MML-AM_CHTML' async></script> 
-->

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/latest.js?config=TeX-MML-AM_CHTML' async></script>
```

下面是显示的情况：

![Image_499](https://gitee.com/gdhu/prvpic/raw/master/Image_499.png)
![Image_501](https://gitee.com/gdhu/prvpic/raw/master/Image_501.png)


## Sublime 中显示公式 

下载并安装MarkDownPreView

下面是一些设置：

```
{
    "browser": "chrome",//设置显示的浏览器
  
    "enable_mathjax": true,//支持公式

    "enable_highlight": true,//支持语法高亮

    "enable_uml": true,//支持UML
}
```

设置快捷键F6: keybindings

```
    { 
    "keys": ["f6"], 
    "command": "markdown_preview", 
    "args": { 
                "target": "browser"
            } 
	}
```

点击F6之后，打开了Chrome浏览器

![Image_500](https://gitee.com/gdhu/prvpic/raw/master/Image_500.png)