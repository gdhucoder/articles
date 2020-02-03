---
title: "HuGo中文章加入目录"
date: 2018-04-04T09:00:00+08:00
draft: false
tags: 
   - TECH
categories:
  - 技术
  - 归档
---

本文介绍如何在template中加入TOC目录。

<!--more-->

# 首先写一个toc.html



如下：

```

{{ if and (gt .WordCount 10 ) (ne .Params.toc "false") }}
<aside>
    <header>
    <h2>{{.Title}}</h2>
    </header>
    {{.TableOfContents}}
</aside>
{{ end }}

```

# 加入到模板single.html中

```
			{{ partial "toc.html" . }}
			{{ .Content }}
```

# 如何升级Hugo

使用choco upgrade(win10)