---
title: "PaperMod 主题常用配置速查"
date: 2026-06-03T16:30:00+08:00
tags: ["hugo", "papermod", "配置", "美化"]
author: "Postman000"
description: "汇总 PaperMod 主题最常用的配置项，方便快速定制自己的博客外观。"
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

## 站点基本信息

```yaml
baseURL: "https://postman000.github.io/"
title: "Postman000 的博客"
paginate: 5
theme: ["PaperMod"]
```

## 首页欢迎语

```yaml
params:
  homeInfoParams:
    Title: "Hi there 👋"
    Content: 欢迎来到我的博客，这里记录我的学习与生活。
```

## 导航菜单

```yaml
menu:
  main:
    - identifier: archives
      name: 归档
      url: /archives/
      weight: 10
    - identifier: tags
      name: 标签
      url: /tags/
      weight: 20
    - identifier: about
      name: 关于
      url: /about/
      weight: 30
```

## 社交图标

```yaml
params:
  socialIcons:
    - name: github
      url: "https://github.com/Postman000"
    - name: twitter
      url: "https://twitter.com/"
    - name: email
      url: "mailto:your@email.com"
```

PaperMod 支持的图标名称可以在主题源码的 `layouts/partials/svg.html` 中查看。

## 文章功能开关

```yaml
params:
  ShowReadingTime: true      # 显示阅读时间
  ShowShareButtons: true     # 显示分享按钮
  ShowPostNavLinks: true     # 显示上一篇/下一篇
  ShowBreadCrumbs: true      # 显示面包屑导航
  ShowCodeCopyButtons: true  # 代码块复制按钮
  ShowWordCount: true        # 显示字数统计
  UseHugoToc: true           # 使用 Hugo 生成的目录
```

## 主题模式

```yaml
params:
  defaultTheme: auto   # auto（跟随系统）、dark、light
  disableThemeToggle: false   # false 允许切换，true 禁止切换
```

## 搜索功能

PaperMod 内置了 Fuse.js 搜索，只需创建 `content/search.md`：

```markdown
---
title: "Search"
layout: "search"
summary: "search"
---
```

然后在菜单中加入搜索入口即可。

## 评论系统（可选）

如果想开启评论，可以在 `params` 中配置，例如使用 Giscus：

```yaml
params:
  comments: true
```

然后在 `layouts/partials/comments.html` 中嵌入 Giscus 脚本（需要自定义主题文件）。

---

> 更多高级玩法可以参考 [PaperMod Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki)。
