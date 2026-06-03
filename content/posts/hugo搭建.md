---
title: "从零搭建 Hugo + PaperMod 博客并部署到 GitHub Pages"
date: 2026-06-03T15:31:30+08:00
tags: ["hugo", "papermod", "github-pages", "教程"]
author: "Postman000"
description: "详细记录如何从零开始搭建一个 Hugo 博客，使用 PaperMod 主题，并部署到 GitHub Pages。"
draft: false
showToc: true
TocOpen: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
UseHugoToc: true
editPost:
    URL: "https://github.com/Postman000/Postman000.github.io/tree/main/content"
    Text: "Suggest Changes"
    appendFilePath: true
---

## 1. 环境安装

### 安装 Hugo

安装过程看官网
后续教程见[快速入门 | Hugo官方文档](https://hugo.opendocs.io/getting-started/quick-start/)
博客主题安装网站(包含教程)
https://github.com/adityatelange/hugo-PaperMod/wiki/Installation

Hugo 是用 Go 语言编写的静态网站生成器，速度极快。安装方式很简单：

**验证安装：**
```bash
hugo version
```

### 创建新站点

```bash
hugo new site MyFreshWebsite
cd MyFreshWebsite
git init
```

### 安装 PaperMod 主题

```bash
cd themes
git clone https://github.com/adityatelange/hugo-PaperMod.git PaperMod
```

然后在 `hugo.yaml` 中加入：
```yaml
theme: ["PaperMod"]
```

### 快速启动预览

```bash
hugo server -D
```

浏览器打开 `http://localhost:1313/` 即可看到效果。

---

## 2. 推送和发布（GitHub Pages）

### 创建 GitHub 仓库

1. 登录 GitHub，新建仓库，命名为 `Postman000.github.io`
2. 如果用户名不同，替换为你自己的用户名

### 配置自动部署

在项目根目录创建 `.github/workflows/deploy.yml`：

```yaml
name: Deploy Hugo site to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.162.1
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v5
      - name: Build with Hugo
        run: hugo --minify --baseURL "${{ steps.pages.outputs.base_url }}/"
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
```

### 推送代码并开启 Pages

```bash
git add .
git commit -m "init blog"
git remote add origin https://github.com/Postman000/Postman000.github.io.git
git push -u origin main
```

然后去 GitHub 仓库设置：
- **Settings → Pages → Source** 选择 **GitHub Actions**
- 等待 Actions 运行完成，访问 `https://postman000.github.io/` 即可

---

## 3. 后续写博客

### 新建文章

使用模板自动生成（推荐）：
```bash
hugo new --kind post posts/我的文章标题.md
```

或者手动在 `content/posts/` 下创建 Markdown 文件。

### 写作 → 预览 → 发布 流程

```bash
# 1. 本地预览
hugo server -D

# 2. 确认无误后提交
git add .
git commit -m "add: 新文章标题"
git push origin main

# 3. GitHub Actions 自动部署，约 1-2 分钟后线上生效
```

### 常用 Front Matter 字段

| 字段 | 说明 |
|---|---|
| `title` | 文章标题 |
| `date` | 发布时间 |
| `tags` | 标签数组 |
| `draft` | `true` 为草稿，不会发布 |
| `description` | 描述，显示在文章列表 |
| `showToc` | 是否显示目录 |

---

## 4. 补充：文件结构、模板与工作流解读

### Hugo 项目文件结构

```
MyFreshWebsite/
├── archetypes/          # 文章模板（hugo new 时自动套用）
├── assets/              # 需要处理的资源（SCSS、JS）
├── content/             # 网站内容（Markdown 文章）
├── data/                # 数据文件
├── layouts/             # HTML 模板（主题会覆盖）
├── static/              # 静态文件（图片、CSS、JS 等直接复制）
├── themes/              # 主题目录
│   └── PaperMod/        # PaperMod 主题文件
├── hugo.yaml            # 站点配置文件
└── .github/workflows/   # GitHub Actions 自动部署脚本
```

### 模板文件（archetypes/post.md）

放在 `archetypes/post.md` 里的内容，会在执行 `hugo new --kind post` 时自动复制到新文章中。通常用来预置常用的 Front Matter，比如作者名、标签、编辑链接等。

### 自动化工作流解读

`.github/workflows/deploy.yml` 做了这几件事：

1. **触发时机**：`push` 到 `main` 分支时自动运行
2. **安装 Hugo**：在 Ubuntu 服务器上安装和你本地相同版本的 Hugo
3. **检出代码**：把你的仓库代码拉下来
4. **构建站点**：执行 `hugo --minify`，生成 `public/` 目录
5. **上传产物**：把 `public/` 打包成 artifact
6. **部署到 Pages**：调用 GitHub Pages 官方 action，把 artifact 发布上线

整个过程是**全自动**的，你只需要专注写作和 `git push`，部署完全不用管。

---
<!-- 
> 有问题欢迎去我的 GitHub 交流：[github.com/Postman000](https://github.com/Postman000) -->
