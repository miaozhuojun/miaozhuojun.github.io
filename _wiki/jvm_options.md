---
layout: wiki
title: JVM 命令和选项
categories: JVM
description: JVM 调测和选项
keywords: JVM，调测，选项
---

### 使用的编译模式

- 纯解释执行

  ```
  -Xint
  ```

### 编译 JDK

- 构建可调试版本

  ```shell
  bash ./configure --with-debug-level=fastdebug --with-native--debug-symbols=internal
  make images CONF=fastdebug
  ```

### 基本测试

- 在 configure 前指 jtreg

  设置环境变量 JT_HOME 为 jtreg 的安装路径

- 执行测试

  ```shell
  make test TEST="tier1"
  ```
