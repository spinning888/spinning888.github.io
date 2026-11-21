---
title: 写作指南：如何在这个博客发文章
description: 新建文章、插入图片、代码、公式的方法（写给自己看的说明书）
slug: how-to-write
date: 2026-10-20
categories:
    - 建站
tags:
    - 博客
    - Markdown
---

这篇是写给自己的“说明书”，忘了怎么发文章就来这里看。

## 新建一篇文章

在 `content/post/` 下面新建一个文件夹，名字用英文，比如 `my-first-note`，里面放一个 `index.md`：

```text
content/post/my-first-note/
├── index.md      ← 文章正文
└── cover.jpg     ← 封面图（可选）
```

`index.md` 开头这一段叫 **front matter**，用来写标题、日期、分类等信息：

```yaml
---
title: 文章标题
description: 一句话简介，会显示在首页卡片上
slug: my-first-note        # 网址，会变成 /p/my-first-note/
date: 2026-11-01
image: cover.jpg           # 封面图，没有就删掉这一行
math: true                 # 需要数学公式才写
categories:
    - 算法
tags:
    - 二分
    - C++
draft: false               # 写成 true 就不会发布
---
```

下面接着写正文就行。

## 插入图片

把图片放在文章文件夹里，然后：

```markdown
![图片说明](图片文件名.png)
```

## 代码块

用三个反引号包起来，并写上语言名，就会有语法高亮：

````markdown
```python
print("Hello")
```
````

## 数学公式

在 front matter 里加上 `math: true`，然后：

- 行内公式：`$E = mc^2$`
- 独立公式：用 `$$ ... $$` 包起来

## 提示框

```markdown
> [!TIP]
> 这是一个提示框
```

效果：

> [!TIP]
> 这是一个提示框

## 发布

保存后推送到 GitHub，大约一两分钟后网站会自动更新。也可以直接在 GitHub 网页上新建或编辑文件。
