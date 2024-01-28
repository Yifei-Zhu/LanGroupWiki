---
layout: page
title: How to start
author: Yifei Zhu
comments: true
tags:
 - Author Guidelines
---
## Editing Wiki {#wiki}
Authors should submit **`Markdown`** files, For text syntax, please refer to the [official documentation](https://markdown.com.cn/intro.html).

!!! tldr "Naming of Markdown Files"
    To felicitating management and because the URLs can become very complex with Chinese, please name the Wiki in the following format:`[Your name in English]_[English document name].md`，for example, 卢璟泽's "批量计算二面角键角键长代码的使用.md" should be renamed to something like `lujz_internal_coordinate.md`.

When editing `Markdown` files locally, it is recommended to use [VSCode](https://code.visualstudio.com/).
Some recommended VSCode extensions include:

- ***All you need for Markdown:*** Provides many useful features, such as quick preview, table formatting, auto-completion, table of contents generation, etc.
- ***Markdownlint:*** Used for checking and correcting syntax and style errors in `Markdown` files.
- ***Prettier:*** Used for automatically formatting `Markdown` files to maintain a consistent style.
- ***Markdown Preview Enhanced:*** Provides enhanced `Markdown` preview capabilities, supporting extended features like mathematical formulas, flowcharts, sequence diagrams, etc.
- ***Code Spell Checker:*** Used for checking spelling errors in `Markdown` files.
- ***Markdown PDF:*** Converts `Markdown` files to PDF format.

Everyone can choose plugins to assist in editing, including but not limited to those mentioned, according to your own needs.

## Upload Wiki

**Method 1**: Please send the edited `Markdown`` file via email to the project [group's email](mailto:zhuyifei.phil@gmail.com).

**Method 2**：Directly operate on the Gitee/GitHub repository using **Pull Requests**.
You will need to learn how to use `Git` on your own.
For guidance, you can refer to [Elegantly Using Gitee/GitHub for Wiki Collaboration](./submit_wiki_en.md).

It is recommended to use the **Method 2** for more convenient management.


## YAML Front Matter
You must include **YAML Front Matter** at the top of your `Markdown` file to enable the `mkdocs.yml` file written in YAML to correctly process the file.

Please add at least the following elements at the top of your file:

### Title & Author
Example:
```YAML
---
title: How to start?
author: Yifei Zhu
---
```

### Tags
Please include tags, for instance:
```YAML
---
...
tags:
  - Python
  - Numpy
---
```
Tags are like the Keywords of an article, which can help us in effective retrieval and classification.
Please try to use the [Tags already used in this Wiki](../tags.md).
If you want to use a new tag, please use the standard name of the software, method, or module as much as possible (be mindful of case sensitivity).

### Comments
Under normal circumstances, please enable the comment function, so that readers can quickly submit feedback or comments.
```YAML
---
...
comments: true
---
```
## File Download
Currently, files for download are uniformly placed in the `/docs/downloads` directory, while Wiki `Markdown`` files are located in `/docs/wiki/[subdir]`.
If you wish to provide a file for download, please write the file path as `../../downloads/[filename]`.

For example:
```Markdown
[Test PDF](../../downloads/download_test.pdf)
```
[Test PDF](../../downloads/download_test.pdf)

Due to the limited capacity of Gitee/GitHub repository, it is currently not recommended to directly upload large files.
We will address this need in the future by renting servers.

Currently, for uploading large files, it is suggested to provide a download link, such as a Baidu Cloud link (note that the extraction code can be provided by directly add `?pwd=[password]` to the URL, the extraction code can be automatically entered). Example:

```Markdown
[Download GaussianView Software](https://pan.baidu.com/s/1Dczutuc1fMJT5vJX64YB0Q?pwd=5zy3)
```
[Download GaussianView Software](https://pan.baidu.com/s/1Dczutuc1fMJT5vJX64YB0Q?pwd=5zy3)


## Inserting Images
### Basic Syntax
```HTML
![Image Description](Image URL)
```
Currently, in each subdirectory, images are uniformly placed in the `./images` directory.
Therefore, the path of a image should be written as `./images/[filename]`.

Here, we take the classical image "Lenna" as an example:
```Markdown
![Lenna](./images/lenna.jpg)
```

![Lenna](./images/lenna.jpg)

### Image Centering
`Markdown` is primarily used for simple text formatting, but it supports the direct use of HTML.
You can use HTML to achieve center alignment for images.

It's important to note that when using HTML block tags, you must add a blank line before and after them for content separation. Additionally, you should not use `tab` or `space` for indenting the opening and closing tags of these elements.

```HTML
<!--a blank line -->
<p align="center">
  <img src="./images/lenna.jpg" alt="It is a classical image.">
</p>
<!--a blank line -->
```

<p align="center">
  <img src="./images/lenna.jpg" alt="It is a classical image.">
</p>


## Inserting Videos
The insertion of videos also requires the use of HTML.
Here, it is recommended using video links provided by third-party video hosting services such as *bilibili*.
For example, we wish to insert the **【官方双语】贝叶斯定理的简洁证明** provided by the official Chinese account of **3Blue1Brown** into our `Markdown` file.

```HTML
<!--a blank line -->
<div style="text-align:center;">
  <iframe width="720" height="405"  src="//player.bilibili.com/player.html?aid=84799859&bvid=BV1o7411a76m&cid=145676706&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>
<!--a blank line -->
```

<div style="text-align:center;">
  <iframe width="752" height="423"  src="//player.bilibili.com/player.html?aid=84799859&bvid=BV1o7411a76m&cid=145676706&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>

## Mathematical Formula
Formula can be inserted using LaTex syntax, please refer to [Formula Handbook](https://www.cnblogs.com/1024th/p/11623258.html).

Some Python libraries ([`latexify-py`](https://github.com/google/latexify_py.git), [handcalcs](https://github.com/connorferster/handcalcs.git), etc.) may be helpful due to the complex syntax of editing formula in LaTex.

## Citing a Section in the Same Wiki
While citing a subsection (second to sixth level headings) in the same Wiki Markdown file, please use **custom anchor** to ensure the stability in collaborative development.
You can directly add `{#custom-anchor}` after the normal title:

```HTML
<!-- Defining  -->
## Editing Wiki {#wiki}
<!-- Citing -->
[Jump the "Editing Wiki" section]({#wiki})
```
[Jump the "Editing Wiki" section](#wiki)

## Additional Notes
  - Please specify the versions of software used, libraries called, etc. If not indicated, it is assumed to be the latest version.
  - All the contents related to the Wiki (including uploaded codes) should be written in a standardized manner. If you are unsure about how to write in a standardized manner, you can refer to the examples or guidelines we provide. For example, *[How to Write Python Code in a Standardized Manner?](./python_standard_en.md)*
