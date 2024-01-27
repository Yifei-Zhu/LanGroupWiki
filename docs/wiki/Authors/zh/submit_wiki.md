---
layout: page
title: 优雅地使用 Gitee/GitHub 参与 Wiki 协作
author: Yifei Zhu
comments: true

---
本文针对于使用 Gitee 或 GitHub 参与本 Wiki 项目管理的基本教学，关于 Gitee 或 GitHub 及 Git 命令的使用可以参考以下文档：

- [Gitee 入门教程](https://gitee.com/mvphp/start_with_Gitee)
- [GitHub 官方文档](https://docs.github.com/zh)
- [Nulab Git 教程](https://nulab.com/zh-cn/learn/software-development/git-tutorial/)

两个平台使用方法基本上没有区别，相互间也很容易实现镜像同步。
原则上可以根据个人喜好选择，~~但如果不科学上网的话 GitHub 的使用会有问题。~~
本 wiki 文档所在仓库托管在 Gitee 平台，因此推荐使用 Gitee 平台，**本文针对 Gitee 平台情况进行说明**。

由于大家使用的熟练程度不同，所以本 Wiki 项目仓库未对所有人开放权限，而仅将部分人列为协作者（ collaborator ）。
本文将针对两种情况分别介绍基本使用方法以供快速检索，**但如果你是协作者请认真学习 Git 命令！**

## 普通用户
### Step1: Fork wiki 文档所在仓库
首先 fork 我们的 wiki 文档所在的 [Gitee 仓库](https://gitee.com/LanGroup/LanGroupWiki.git)到你的 Gitee 账户下。

此时，可以通过点击 *Upload files* 或拖拽的方式上传编辑好的文件及附件。如果直接通过这种方式提交你的更新，直接跳到 [Step7](#PR) 。

!!! tldr "文件路径"
    - Markdown 文件请放在 wiki 目录下相应模块的子目录中
    - 图片请放在相应子目录下的`images`路径下
    - 如需上传供下载的附件请放在`downloads`路径下

!!! error "文件路径"
    - Markdown 文件请放在 wiki 目录下相应模块的子目录中
    - 图片请放在相应子目录下的`images`路径下
    - 如需上传供下载的附件请放在`downloads`路径下

### Step2:克隆仓库
!!! tldr "Git 全局设置"
    如果首次在计算机上配置 Git 时，需要先进行 Git 全局设置：
    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your_email@example.com"
    ```

使用`git clone`命令克隆你刚 fork 的仓库到本地计算机。
```bash
git clone git@github.com:Yifei-Zhu/LanGroupWiki.git
```
`git clone`会自动设置远程仓库，并将其默认命名为 **origin** 。

### Step3:创建新分支
在本地仓库中，创建一个新分支进行你的更改。
```bash
git checkout -b <新分支名称>
```
!!! tldr "Note"
    Step3 也可以跳过，推荐大家规范化在分支进行修改。

### Step4:进行更改并提交
在新分支上进行必要的更改。
注意，如果增删内容，请在`mkdocs.yml`做对应修改，比如你希望在 **软件使用** 模块新增一个关于 Gaussian 程序使用的说明，将 *Gaussian_guide.md* 文件置于 *./wiki/Software_guide* 目录下后，你需要在`mkdocs.yml` **软件使用** 下增加该文件路径（注意缩进以及以 - 开头），比如：
```YAML
- 软件使用:
    ......（其他文件路径）
    - ./wiki/Software_guide/Gaussian_guide.md
    ......（其他文件路径）
```

可以启动一个本地 Web 服务器（默认为`http://127.0.0.1:8000`）实时预览，可以通过`--dev-addr=`选项修改本地开发服务器的地址和端口。
```bash
mkdocs serve
mkdocs serve --dev-addr=<IP地址>:<端口号>
```

### Step5: 提交你的修改
使用`git add`和`git commit`命令将更改提交到你的分支。

```bash
git add .
git commit -m "描述你的更改"
```

### Step6:推送到你的 Fork
使用`git push`将更改推送到你的 fork 。
```bash
git push origin <新分支名称>
```

### Step7:发起 Pull Request {#PR}

- 在你的 Gitee 仓库页面上，转到 **Pull requests** 选项卡并点击 **New pull request** 。
- 选择你刚刚推送的分支，并点击 **Create pull request** 按钮。
- 填写 **Pull Request** 的标题和描述，然后提交。

## 协作者
协作者因为有修改原仓库的权限，因此不需要 **Pull Request** 。大概流程如下：
### Step1:克隆仓库

### Step2：进行更改并本地测试

### Step3：提交和推送更改：
使用 Git 命令（`git add`、`git commit`和`git push`）将更改提交并推送到远程仓库。
!!! tldr "Note"
    当你发布一个新的版本时，推荐使用`git tag`命令为该版本创建标签并添加说明。

```bash
git add .
git commit -m "描述你的更改"
git tag <标签名称>
git tag -a <标签名称> -m "标签信息"
git push origin <标签名称>
```

### *Step4：部署到 Gitee/GitHub Pages
可以运行`mkdocs gh-deploy`。这个命令会自动构建网站，并将生成的文件推送到 **gh-pages** 分支。
```bash
mkdocs gh-deploy
```

