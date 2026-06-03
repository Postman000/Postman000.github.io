---
title: "你好，世界！我的第一篇博客"
date: 2026-06-03T08:00:00+08:00
tags: ["hugo", "papermod", "beginner"]
categories: ["测试"] 
author: "Me"
description: "这是一篇示例文章，介绍如何开始使用 Hugo + PaperMod 写博客。"
draft: false
showToc: true
TocOpen: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
UseHugoToc: true
---

## 欢迎来到我的博客

这是我的第一篇博客文章！🎉

我正在使用 **Hugo** 静态网站生成器和 **PaperMod** 主题来搭建这个博客。

### 为什么选 Hugo？

- ⚡ **速度极快**：每秒可以生成数千页面
- 📝 **用 Markdown 写作**：专注内容，不用管排版
- 🎨 **主题丰富**：PaperMod 就是一款非常简洁美观的主题
- 🚀 **部署简单**：生成的是纯静态文件，到处都能托管

### 这篇文章的 Front Matter

你看到文章开头被 `---` 包裹的部分叫 **Front Matter**，它是这篇文章的"元信息"：

| 字段 | 作用 |
|---|---|
| `title` | 文章标题 |
| `date` | 发布日期 |
| `tags` | 标签，用逗号分隔 |
| `author` | 作者名 |
| `description` | 文章描述，会显示在列表页 |
| `draft` | `true` 表示草稿，不会发布 |
| `showToc` | 是否显示目录（Table of Contents） |

### 代码块示例

```python
print("Hello, Hugo + PaperMod!")
```

### 接下来做什么？

1. 修改 `hugo.yaml` 里的 `title`、`author`、`homeInfoParams` 为你自己的信息
2. 在 `content/posts/` 目录下新建 `.md` 文件写文章
3. 运行 `hugo server -D` 本地预览
4. 满意后部署到 GitHub Pages / Vercel 等平台

---

> 感谢阅读！欢迎继续探索 Hugo 的世界。
