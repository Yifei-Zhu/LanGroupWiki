---
layout: page
title: How to Use Markdown
author: Yifei Zhu
comments: true
tags:
 - Author Guidelines
 - Markdown
---

## Miscellaneous
In this section, we do not delve into [the basic syntax of Markdown](https://markdown.com.cn/intro.html).
Instead, our emphasis is on introducing commonly used extended syntax.

### Task Checklist
```Markdown
<!-- (blank line) -->
- [x] Completed
- [ ] Uncompleted
```

- [x] Completed
- [ ] Uncompleted

### 提示
```Markdown
!!! tldr "A title"
    Some contents
```
!!! tldr "A title"
    Some contents

Here, `tldr` can be replaced by other keywords to create various types of tooltips:

```Markdown
!!! success "A title"
    Some contents
```
!!! success "A title"
    Some contents

```Markdown
!!! tip "A title"
    Some contents
```
!!! tip "A title"
    Some contents

```Markdown
!!! info "A title"
    Some contents
```
!!! info "A title"
    Some contents

```Markdown
!!! question "A title"
    Some contents
```
!!! question "A title"
    Some contents

```Markdown
!!! warning "A title"
    Some contents
```
!!! warning "A title"
    Some contents

```Markdown
!!! danger "A title"
    Some contents
```
!!! danger "A title"
    Some contents

### Button
```Markdown
[Our Wiki Home](../../index.md){ .md-button }
```
[Our Wiki Home](../../index.md){ .md-button }

