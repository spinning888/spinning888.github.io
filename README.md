# 我的学习笔记

线上地址：https://spinning888.github.io/

从导出的“个人学习网站搭建”记录恢复暖色版本，保留四篇示例文章；头像以同配色 SVG 重建。

基于 [Hugo](https://gohugo.io/) 和 [Stack 主题](https://github.com/CaiJimmy/hugo-theme-stack) 的个人学习博客。不需要服务器和后端，托管在 GitHub Pages 上，完全免费。

推送到 GitHub 后，GitHub Actions 会自动构建网站并发布，**你的电脑上不需要安装任何东西**。

---

## 一、部署到 GitHub Pages（只需做一次）

### 1. 新建仓库

登录 GitHub，点右上角 **+ → New repository**：

- **Repository name** 填 `spinning888.github.io`，例如用户名是 `xiaoming`，就填 `xiaoming.github.io`
- 选择 **Public**
- 其他保持默认，点 **Create repository**

> 仓库也可以用其他名字（比如 `blog`），这样网址会变成 `https://spinning888.github.io/blog/`，构建时会自动适配，不用改配置。

### 2. 上传文件

**方法 A：用 Git 命令（推荐）**

在这个文件夹里打开终端：

```bash
git init
git add .
git commit -m "初始化博客"
git branch -M main
git remote add origin https://github.com/spinning888/spinning888.github.io.git
git push -u origin main
```

**方法 B：用 GitHub Desktop**

安装 [GitHub Desktop](https://desktop.github.com/)，选择 **File → Add local repository**，选中这个文件夹，然后点 **Publish repository**。

> ⚠️ 不建议在网页上拖拽上传：`.github` 是隐藏文件夹，很容易漏传，而自动部署全靠它。

### 3. 打开 Pages

进入仓库的 **Settings → Pages**，把 **Build and deployment → Source** 改成 **GitHub Actions**。

### 4. 等待部署

点仓库顶部的 **Actions** 标签，可以看到 “Build and deploy” 正在运行。变成绿色 ✅ 后（大约 1 到 2 分钟），访问 `https://spinning888.github.io` 就能看到网站了。

如果第一次运行发生在第 3 步之前而失败了，在 Actions 里点开失败的那次运行，点 **Re-run all jobs** 即可。

---

## 二、改成你自己的

| 想改什么 | 改哪个文件 |
| --- | --- |
| 网站标题、页脚名字 | `config/_default/config.toml` 里的 `title`、`copyright` |
| 头像 | 替换 `assets/img/avatar.svg`（正方形图片） |
| 网站小图标 | 替换 `assets/img/favicon.svg` |
| 头像旁的表情、个性签名 | `config/_default/params.toml` 里的 `[sidebar]` |
| 建站日期（“已稳定运行 X 天”） | `config/_default/params.toml` 里的 `startDate` |
| GitHub 等社交链接 | `config/_default/menu.toml` |
| 关于页 | `content/page/about/index.md` |
| 友链 | `content/page/links/index.md` |
| 分类的颜色和介绍 | `content/categories/分类名/_index.md` |
| 自定义样式 | `assets/scss/custom.scss` |

改完后提交并推送，网站会自动更新。

---

## 三、写文章

在 `content/post/` 下新建一个英文名的文件夹，里面放 `index.md`：

```text
content/post/my-note/
├── index.md
└── cover.jpg   （封面图，可选）
```

`index.md` 的开头：

```yaml
---
title: 文章标题
description: 一句话简介
slug: my-note
date: 2026-11-01
image: cover.jpg
categories:
    - 算法
tags:
    - C++
---

正文从这里开始……
```

更多写法（图片、代码、数学公式、提示框）见网站上的《写作指南》这篇文章（`content/post/how-to-write/index.md`）。

> 💡 **不想用命令行？** 可以直接在 GitHub 网页上进入 `content/post/`，点 **Add file → Create new file**，文件名写 `my-note/index.md`，写好后点 **Commit changes**，网站就会自动更新。

示例文章看完可以直接删掉对应的文件夹。

---

## 四、本地预览（可选）

想在自己电脑上边写边看效果，需要安装 [Git](https://git-scm.com/)、[Go](https://go.dev/dl/) 和 [Hugo extended 版](https://gohugo.io/installation/)，然后在这个文件夹里运行：

```bash
hugo server
```

打开 `http://localhost:1313` 即可，保存文件后页面会自动刷新。

也可以在 GitHub 仓库页面点 **Code → Codespaces → Create codespace**，在浏览器里得到一个已经配好环境的编辑器，直接运行 `hugo server`。

---

## 五、进阶

### 绑定自己的域名

1. 在域名服务商处添加一条 **CNAME** 记录，指向 `spinning888.github.io`
2. 在仓库 **Settings → Pages → Custom domain** 填入你的域名，保存后勾选 **Enforce HTTPS**

### 开启评论区

推荐 [giscus](https://giscus.app/zh-CN)（基于 GitHub Discussions，免费）：

1. 在仓库 **Settings → General → Features** 勾选 **Discussions**
2. 打开 giscus.app，按页面提示填写仓库名，得到 `repoID`、`categoryID` 等值
3. 填到 `config/_default/params.toml` 的 `[comments.giscus]` 里，并把 `[comments]` 下的 `enabled` 改成 `true`

### 主题更新

主题固定为 Stack v4.0.3，Hugo 固定为 0.158.0。更新主题前先本地构建验证。

---

## 致谢

- 主题：[Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack)，作者 Jimmy Cai（GPL-3.0）
- 起始模板：[hugo-theme-stack-starter](https://github.com/CaiJimmy/hugo-theme-stack-starter)（MIT）
- 示例封面图来自 [Unsplash](https://unsplash.com/)
