---
layout: page
title: 作者须知
author: Yifei Zhu
comments: true
tags:
  - 作者须知
---  
  
  
  
  
  
  
  
  
## Markdown
  
### 编辑Wiki
作者须提交`Markdown`文件，文本语法请查看[官方文档](https://markdown.com.cn/intro.html )。
  
在本地编辑`Markdown`文件时，推荐使用[VSCode](https://code.visualstudio.com/ )。
一些推荐的VSCode插件包括：
  
- ***All you need for Markdown:*** 提供了许多实用的功能，如快速预览、表格格式化、自动补全、目录生成等。
- ***Markdownlint:*** 用于检查和纠正`Markdown`文件中的语法和风格错误。
- ***Prettier:*** 用于自动格式化`Markdown`文件，使其保持一致的风格。
- ***Markdown Preview Enhanced:*** 提供了更强大的`Markdown`预览功能，支持数学公式、流程图、时序图等扩展功能。
- ***Code Spell Checker:*** 用于检查`Markdown`文件中的拼写错误。
- ***Markdown PDF:*** 将`Markdown`文件转换为 PDF 格式。
  
大家可以根据自己的情况选择包括不仅限于此的插件辅助编辑。
  
### 上传Wiki
方式1：推荐`pull requests`的直接增删Github仓库，需自行学习git的使用。
  
方式2：请将编辑好的`Markdown`文件发送给
  
  
  
## YAML Front Matter
只有在`Markdown`文件的头部加入`YAML Front Matter`部分，才能使你写的 Wiki展示在网页上。
请在你的Wiki文件头部至少加入以下元素
  
### title&author
示例：
```
---
title: 作者须知
author: Yifei Zhu
---
```
  
### tags
请尽量加入tags，如：
  
```
---
...
tags:
  - Python
  - Numpy
---
```
Tags就像文章的Keywords，可以帮助我们有效检索及分类。
请尽量使用本Wiki已使用的[Tags](wiki/tags.md )，如果希望使用新的Tag，请尽量使用该软件、方法、模块的标准名称（注意大小写）。
  
###comments
通常情况下请开启评论功能、以便读者可以快速提交反馈或评论。
```
---
...
comments: true
---
```
  