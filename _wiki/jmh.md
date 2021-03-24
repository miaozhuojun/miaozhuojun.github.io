---
layout: wiki
title: JMH 命令和选项
categories: JMH
description: JMH 命令和选项
keywords: JMH，选项
---

### 设置测试次数

- 设置余热次数`-wi <int>`
- 设置测量迭代次数`-i <int>`
- 设置 fork 次数，每次 fork 中进行 n 次迭`-f <int>`

### 设置待测的 JVM

`-jvm <string>`

### 设置 JVM 选项

- 为给定 JVM 设置启动参数：`-jvmArgs <string>`

### 可视化 JMH 结果

- 首先需要将 JMH 结果以 json 格式生成：`-rf json -rff <string.json>`
- 将生成的文件输入 [jmh-visual-char](https://github.com/Sayi/jmh-visual-chart) 中
