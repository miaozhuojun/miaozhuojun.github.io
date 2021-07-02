---
layout: wiki
title: JMH
categories: JMH
description: JMH 命令和选项
keywords: JMH，选项
---

### 设置测试次数

- 设置预热次数`-wi <int>`
- 设置测量迭代次数`-i <int>`
- 设置 fork 次数，每次 fork 中进行 n 次迭`-f <int>`

### 设置待测的 JVM

`-jvm <string>`

### 设置 JVM 选项

- 为给定 JVM 设置启动参数：`-jvmArgs <string>`

### 可视化 JMH 结果

- 首先需要将 JMH 结果以 json 格式生成：`-rf json -rff <string.json>`
- 将生成的文件输入 [jmh-visual-char](https://github.com/Sayi/jmh-visual-chart) 中

### Maven 构建时从本地获取依赖的 jar 包

背景：由于在构建关于 BLAS 的 JMH 工程时需要依赖 netlib 库，而这个库默认不包含 aarch64 平台的 jar 包，所以需要手工将 jar 包放到本地，然后让 Maven 引入依赖。

- 首先使用`mvn install`命令将本地 jar 包安装到 maven 仓库

  ```shell
  mvn install:install-file -Dfile=<path to local jar file> -DgroupId=com.github.fommil.netlib -DartifactId=netlib-native-system-linux-aarch64 -Dversion=1.1 -Dpackaging=jar
  ```

- 然后修改~/.m2/repository/com/github/fommil/netlib/all/1.1.2/all-1.1.2.pom

  插入如下依赖

  ```pom
  <dependency>
    <groupId>com.github.fommil.netlib</groupId>
    <artifactId>netlib-native-system-linux-aarch64</artifactId>
    <version>1.1</version>
    <classifier>natives</classifier>
  </dependency>
  ```

- 最后构建 JMH 工程

  ```shell
  mvn clean package
  ```

### make 直接跑 jmh

[Testing the JDK](https://openjdk.java.net/groups/build/doc/testing.html)

`make test TEST="micro:java.lang.StringEquals" MICRO="VM_OPTIONS=-XX:+UseSimpleStringEquals" CONF=fastdebug`
