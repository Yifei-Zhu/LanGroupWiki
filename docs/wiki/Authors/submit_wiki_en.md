---
layout: page
title: Elegantly Using Gitee/GitHub for Wiki Collaboration
author: Yifei Zhu
comments: true
tags:
 - Author Guidelines
 - Git
---
This wiki provdes a basic tutorial for managing this Wiki project using Gitee or GitHub.
For more comprehensive information on using Gitee or Github, as well as Git command, you can refer to the following documents:

- [Gitee Getting Started Tutorial](https://gitee.com/mvphp/start_with_Gitee)
- [GitHub Official Documentation](https://docs.github.com/zh)
- [Nulab Git Toturial](https://nulab.com/zh-cn/learn/software-development/git-tutorial/)

The usage of GitHub and Gitee platforms is essentially the same, and it is also easy to achieve mirror synchronization between them.
In principle, one can choose according to personal preference.
~~However, it is difficult to directly access Github without **科学上网**.~~
The repository for this wiki documentation is hosted on the Gitee platform, so it is recommended to use the Gitee platform.
This article provides instructions specific to the Gitee platform.

Due to varying levels of proficiency among users, the permissions of our repository are not entirely opened to everyone.
Instead, only a few individuals are designated as *Administrators*.
Here, we provide an introduction to basic usage methods for both *Administrator* and *Commen User* for quick reference.
**However, if you are designated as a *Administrator*, please take the time to systematically study Git commands.**

## Commen User
### Step1: Fork the repository of this Wiki
First of all, you should fork the [Gitee repository](https://gitee.com/LanGroup/LanGroupWiki.git) where our wiki documentations are located to your Gitee account.

At this point, you can certainly upload the edited files and attachments by clicking on *Upload files* button or by dragging and dropping.
If you choose to do so, please skip steps 2-6 and proceed directly to [Step7](#PR) to **Pull Request** to submit your updates.

!!! tldr "File Path"
    - Please place the Markdown file in the `/docs/wiki/[module]` subdirectory of the specific module under the wiki directory.
    - Please place the images in `/docs/wiki/[module]/images` folder of the corresponding subdirectory.
    - If you need upload other attachments for downloading, please place them in `/docs/downloads` directory.

### Step2: Clone the repository to your local machine.
!!! tldr "Git Global Configuration"
    If configuring Git on your local machine for the first time, you need to perform Git global configuration:
    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your_email@example.com"
    ```
Clone the repository that you already forked to your local machine using the `git clone` command.
```bash
git clone git@github.com:Yifei-Zhu/LanGroupWiki.git
```
The `git clone` command automatically adds the remote repository (by dafultly named as **origin** ).

### Step3: Create new branch
In the local repository, creat a new branch for your changes using `git checkout` command.
```bash
git checkout -b <New branch>
```
!!! tldr "Note"
    The Step3 is not mandatory and can be skipped, but it is recommanded that everyone follows best practices by making changes in branches to ensure the stability of the `master` branch.

### Step4: Make changes
If your changes are not limited to the existing files,  but rather adding or deleting certain content, please make corresponding modifications in `mkdocs. yml` file.

For example, if you wish add a wiki about the instruction of Gaussian software in **Software Usage** module, you should place the *Gaussian_guide.md* file under *./wiki/Software_guide* directory.
Then, you need to add the relative path of this file by modifying the **Software Usage** section in the `mkdocs.yml` file.
Note that this path should be started with - and follow specifc indentation, as shown below:
```YAML
- Software Usage:
    ......（Other file paths）
    - ./wiki/Software_guide/Gaussian_guide.md
    ......（Other file paths）
```

You can start a local web serve using `mkdocs serve` to real-time preview your changes.
The default address and port is `http://127.0.0.1:8000`, which can be modified using the `--dev-addr=` option.
```bash
mkdocs serve
mkdocs serve --dev-addr=<IP地址>:<端口号>
```

!!! tldr "Installation of MkDocs with Material for MkDocs Theme"
    Our wiki are setted up by using MkDocs with the Material for MkDocs theme, which can be installed by command-line commands:
    ```bash
    pip install mkdocs mkdocs-material
    ```
    Then you can verify the installation by:
    ```bash
    mkdocs --version
    ```

### Step5: Commit changes
Use the `git add` and `git commit` commands to commit your changes to your working brach.
```bash
git add .
git commit -m "description of your changes"
```

### Step6: Push changes
Use the `git push` command to push your changes to remote repository you forked.
```bash
git push origin <working branch name>
```

### Step7: Create a Pull Request {#PR}
- On your Gitee repository page, click the **+ Pull requests** button.
- Select the branch you just pushed as the source branch, fill in the title and description about the changes you made.
- Click the **Create a pull request draft** to preview the merged version.
- If everything is fine, click the **Create pull request** button.

## Administrator
Since administrator have the authority to make changes directly in the original repository, there is no need to perform **Pull Request**.
The workflow is outlined below:
### Step1: Clone the repository to your local machine.

### Step2：Make changes and preview locally.

### Step3：Commit and push changes.
Use Git commands (`git add`, `git commit` and `git push`) to commit and push changes to remote repository to merge your changes with original version.

!!! tldr "Note"
    When you try to release a new version with many changes, it is recommended to use `git tag` to create a tag for that version and add a description for these changes.

```bash
git add .
git commit -m "description about changes"
git tag <tag name>
git tag -a <tag name> -m "description about changes"
git push origin <tag name>
```

### *Step4：Deploy to Gitee/GitHub Pages
You can run `mkdocs gh-deploy` command to build the website via Gitee/GitHub Pages, and automatically push the files to **gh-pages** branch of remote repository.
```bash
mkdocs gh-deploy
```

