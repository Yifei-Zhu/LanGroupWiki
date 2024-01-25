---
layout: page
title: 开始编辑（必读）
author: Yifei Zhu
comments: true
tags:
 - 作者须知
---
## 编辑Wiki {#wiki}
作者须提交 Markdown 文件，文本语法请查看[官方文档](https://markdown.com.cn/intro.html)。

在本地编辑 Markdown 文件时，推荐使用 [VSCode](https://code.visualstudio.com/) 。
一些推荐的 VSCode 插件包括：

- ***All you need for Markdown:*** 提供了许多实用的功能，如快速预览、表格格式化、自动补全、目录生成等。
- ***Markdownlint:*** 用于检查和纠正 Markdown 文件中的语法和风格错误。
- ***Prettier:*** 用于自动格式化 Markdown 文件，使其保持一致的风格。
- ***Markdown Preview Enhanced:*** 提供了更强大的 Markdown 预览功能，支持数学公式、流程图、时序图等扩展功能。
- ***Code Spell Checker:*** 用于检查 Markdown 文件中的拼写错误。
- ***Markdown PDF:*** 将 Markdown 文件转换为 PDF 格式。

大家可以根据自己的情况选择包括不仅限于此的插件辅助编辑。
HH
## 上传Wiki
为方便审核，目前本Wiki推荐方式1。

方式1：请将编辑好的 Markdown 文件通过邮箱发送到[课题组邮箱](mailto:zhuyifei.phil@gmail.com)。

方式2：使用 **pull requests** 的直接操作GitHub仓库，需自行学习Git的使用，可以参见[优雅地使用GitHub参与Wiki协作](./submit_wiki.md)。

## YAML Front Matter
必须在 Markdown 文件的头部加入 **YAML Front Matter** ，才能使由 YAML 写的 `mkdocs.yml` 正确处理该文件。
请在你的文件头部至少加入以下元素：

### title & author
示例：
```YAML
---
title: 作者须知
author: Yifei Zhu
---
```

### tags
请尽量加入 tags ，如：

```YAML
---
...
tags:
  - Python
  - Numpy
---
```
Tags 就像文章的 Keywords ，可以帮助我们有效检索及分类。
请尽量使用[本 Wiki 已使用的 Tags ](../tags.md)，如果希望使用新的 Tag ，请尽量使用该软件、方法、模块的标准名称（注意区分大小写）。

### comments
通常情况下请开启评论功能、以便读者可以快速提交反馈或评论。
```YAML
---
...
comments: true
---
```
## 文件下载
目前，文件统一放置在`/docs/downloads`目录下，而 Wiki 均放在`/wiki/[subdir]`中，因为如想提供文件下载，请将文件路径写成`../../downloads/[filename]`
示例：
```Markdown
[Test Wiki的PDF](../../downloads/download_test.pdf)
```
[Test Wiki的PDF](../../downloads/download_test.pdf)


由于 GitHub 仓库容量有限，暂时不推荐直接上传过大的文件，后续我们会通过服务器完善这方面需求。
目前上传大文件建议通过提供下载链接，如百度云链接(注意，这里的url后直接加上`?pwd=`提取码，即可自动输入提取码)，示例：
```Markdown
[下载 gview 软件](https://pan.baidu.com/s/1Dczutuc1fMJT5vJX64YB0Q?pwd=5zy3)
```
[下载 gview 软件](https://pan.baidu.com/s/1Dczutuc1fMJT5vJX64YB0Q?pwd=5zy3)


## 插入图片
### 基本语法
```HTML
![图片描述](图片URL)
```
目前，在每个子目录中，图片统一放置在`./images`目录下，因为如想提供文件下载，请将文件路径写成`./images/[filename]`

此处我们选取经典图片Lenna作为示例：
```Markdown
![Lenna](./images/lenna.jpg)
```
![Lenna](./images/lenna.jpg)

### 图片居中
Markdown 主要是用于简单的文本格式化，但其支持 HTML 的直接使用，可以使用 HTML 来实现图片的居中。
需注意使用 HTML 区块标签时必须在前后加上空行，以便于内容区分
而且这些元素的开始与结尾标签，不可以用`tab`或是`space`来缩进。

```HTML
（空行）
<p align="center">
  <img src="./images/lenna.jpg" alt="这是一张示例图片">
</p>
（空行）
```

<p align="center">
  <img src="./images/lenna.jpg" alt="这是一张示例图片">
</p>


## 插入视频
视频的插入也需要借助 HTML 语言。
这里我们推荐使用第三方视频托管服务（如 bilibili 等）提供的视频链接。
示例为 **3Blue1Brown** 中国官方账号视频 **【官方双语】贝叶斯定理的简洁证明**。

```HTML
（空行）
<div style="text-align:center;">
  <iframe width="720" height="405"  src="//player.bilibili.com/player.html?aid=84799859&bvid=BV1o7411a76m&cid=145676706&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>
（空行）
```

<div style="text-align:center;">
  <iframe width="752" height="423"  src="//player.bilibili.com/player.html?aid=84799859&bvid=BV1o7411a76m&cid=145676706&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>

## 数学公式
可以用 Latex 语法插入公式，可以参考[公式手册](https://www.cnblogs.com/1024th/p/11623258.html)。
由于其语法比较复杂，也可以使用一些在线的公式编辑器。
还可以使用 Python 的一个库 [`latexify-py`](https://github.com/google/latexify_py.git) 。

## 引用本 Wiki 章节
在引用同一 Wiki 章节（二至六级标题）时，为保证多人共同开发的稳定性，请使用自定义锚点（英文）。定义方式为正常标题后加上`{#custom-anchor}`。示例：
```HTML
<!-- 定义 -->
## 编辑 Wiki {#wiki}
<!-- 引用 -->
[跳转到 Markdown 章节]({#wiki})
```
[跳转到 Markdown 章节]({#wiki})

## 其他注意事项
  - Wiki 中涉及的 **使用的软件、调用的库** 等请注明版本，如不标注，默认为最新版本。
  - Wiki 内容请 **规范书写**，包括上传的代码等请遵循相应的书写规则，比如 Python 代码需要遵循[PEP8规范](https://peps.python.org/pep-0008/)。
