---
layout: page
title: 作者须知
author: Yifei Zhu
comments: true
tags:
 - 作者须知
---
## Markdown {#markdown_tutorial}

### 编辑Wiki
作者须提交`Markdown`文件，文本语法请查看[官方文档](https://markdown.com.cn/intro.html)。

在本地编辑`Markdown`文件时，推荐使用[VSCode](https://code.visualstudio.com/)。
一些推荐的VSCode插件包括：

- ***All you need for Markdown:*** 提供了许多实用的功能，如快速预览、表格格式化、自动补全、目录生成等。
- ***Markdownlint:*** 用于检查和纠正`Markdown`文件中的语法和风格错误。
- ***Prettier:*** 用于自动格式化`Markdown`文件，使其保持一致的风格。
- ***Markdown Preview Enhanced:*** 提供了更强大的`Markdown`预览功能，支持数学公式、流程图、时序图等扩展功能。
- ***Code Spell Checker:*** 用于检查`Markdown`文件中的拼写错误。
- ***Markdown PDF:*** 将`Markdown`文件转换为 PDF 格式。

大家可以根据自己的情况选择包括不仅限于此的插件辅助编辑。

### 上传Wiki
为方便审核，目前本Wiki推荐方式1。

方式1：请将编辑好的`Markdown`文件通过邮箱发送到[课题组邮箱](xxxxx)。

方式2：推荐`pull requests`的直接增删Github仓库，需自行学习git的使用。

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
请尽量使用本Wiki已使用的[Tags](wiki/tags.md)，如果希望使用新的Tag，请尽量使用该软件、方法、模块的标准名称（注意大小写）。

### comments
通常情况下请开启评论功能、以便读者可以快速提交反馈或评论。
```
---
...
comments: true
---
```

## 文件下载
目前，文件统一放置在`/docs/downloads`目录下，而Wiki均放在`/wiki/[subdir]`中，因为如想提供文件下载，请将文件路径写成`../../downloads/[filename]`
示例：
```
[Test Wiki的PDF](../../downloads/download_test.pdf)
```
[Test Wiki的PDF](../../downloads/download_test.pdf)


由于GitHub仓库容量有限，暂时不推荐直接上传过大的文件，后续我们会通过服务器完善这方面需求。
目前上传大文件建议通过提供下载链接，如百度云链接(注意，这里的url后直接加上?pwd=提取码，即可自动输入提取码)，示例：
```
[下载gview](https://pan.baidu.com/s/1Dczutuc1fMJT5vJX64YB0Q?pwd=5zy3)
```
[下载gview](https://pan.baidu.com/s/1Dczutuc1fMJT5vJX64YB0Q?pwd=5zy3)


## 插入图片
### 基本语法
```
![图片描述](图片URL)
```
目前，图片统一放置在`/docs/images`目录下，而Wiki均放在`/wiki/[subdir]`中，因为如想提供文件下载，请将文件路径写成`../../images/[filename]`

此处我们选取经典图片Lenna作为示例：
```
![Lenna](../../images/lenna.jpg)
```
![Lenna](../../images/lenna.jpg)

### 图片居中
`Markdown`主要是用于简单的文本格式化，但其支持HTML的直接使用，可以使用HTML来实现图片的居中。
需注意使用HTML区块标签时必须在前后加上空行，以便于内容区分。而且这些元素的开始与结尾标签，不可以用 tab 或是空白来缩进。

```HTML
（空行）
<p align="center">
  <img src="../../images/lenna.jpg" alt="这是一张示例图片">
</p>
（空行）
```

<p align="center">
  <img src="../../images/lenna.jpg" alt="这是一张示例图片">
</p>


## 其他
`Markdown`的基础语法不再介绍，本部分介绍几个可能会用到的进阶用法。

### 引用本Wiki章节
在引用同一Wiki章节（二至六级标题）时，为保证多人共同开发的稳定性，请使用自定义锚点（英文）。定义方式为正常标题后加上`{#custom-anchor}`。示例：
```
<!-- 定义 -->
## Markdown {#markdown_tutorial}
<!-- 引用 -->
[跳转到Markdown章节]{#markdown_tutorial}
```
[跳转到Markdown章节](#markdown_tutorial)

### 任务清单
```
（空行）
- [ ] 未完成任务
- [x] 已完成任务
```

- [ ] 未完成任务
- [x] 已完成任务

### 提示
```
!!! tldr "标题"
    内容
```
!!! tldr "标题"
    内容

```
!!! tip "标题"
    内容
```
!!! tip "标题"
    内容
```
!!! info "标题"
    内容
```
!!! info "标题"
    内容

```
!!! question "标题"
    内容
```
!!! question "标题"
    内容

```
!!! warning "标题"
    内容
```
!!! warning "标题"
    内容

```
!!! danger "标题"
    内容
```
!!! danger "标题"
    内容

```
!!! success "标题"
    内容
```
!!! success "标题"
    内容

### 按钮
```
[访问我们的Wiki Home](../../index.md){ .md-button }
```
[访问我们的Wiki Home](../../index.md){ .md-button }

