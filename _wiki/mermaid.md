---
layout: wiki
title: mermaid
categories: markdown
description: mermaid 使用相关
keywords: markdown, mermaid，图表
---

## 如何在博客中使用 mermaid 功能

- 在文章头声明开启 mermaid：`mermaid: true`
- 关闭 html 压缩功能，防止 mermaid 语法被破坏
  - 删除_layouts/default.html 的头四行
- 使用较新的 mermaid 版本
  - 修改 _includes/footer.html 文件第 51 行为 `<script src="https://cdn.jsdelivr.net/npm/mermaid@8.5.0/dist/mermaid.min.js"></script>`

## 添加状态转换图

## 参考

