---
title: "Markdown 常用语法速查"
date: 2026-06-03T16:00:00+08:00
tags: ["markdown", "写作", "工具"]
author: "Postman000"
description: "整理 Markdown 最常用的语法，方便日常写作时快速查阅。"
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

## 标题

```markdown
# 一级标题
## 二级标题
### 三级标题
```

## 文本样式

| 效果 | 语法 | 示例 |
|---|---|---|
| 粗体 | `**文字**` | **粗体** |
| 斜体 | `*文字*` | *斜体* |
| 删除线 | `~~文字~~` | ~~删除线~~ |
| 行内代码 | `` `代码` `` | `code` |

## 列表

### 无序列表

```markdown
- 项目一
- 项目二
  - 子项目
```

效果：
- 项目一
- 项目二
  - 子项目

### 有序列表

```markdown
1. 第一步
2. 第二步
3. 第三步
```

## 链接与图片

```markdown
[链接文字](https://example.com)
![图片描述](https://example.com/image.png)
```

## 代码块

````markdown
```python
def hello():
    print("Hello, World!")
```
````

## 引用

```markdown
> 这是一段引用文字。
> 可以有多行。
```

效果：
> 这是一段引用文字。
> 可以有多行。

## 表格

```markdown
| 姓名 | 年龄 | 城市 |
|---|---|---|
| 张三 | 25 | 北京 |
| 李四 | 30 | 上海 |
```

效果：

| 姓名 | 年龄 | 城市 |
|---|---|---|
| 张三 | 25 | 北京 |
| 李四 | 30 | 上海 |

## 分隔线

```markdown
---
```

效果：

---

## 任务列表

```markdown
- [x] 已完成任务
- [ ] 未完成任务
```

效果：

- [x] 已完成任务
- [ ] 未完成任务

---

> 熟练掌握这些语法，足够应对 99% 的写作场景。
