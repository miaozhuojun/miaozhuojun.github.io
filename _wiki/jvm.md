---
layout: wiki
title: JVM
categories: JVM
description: JVM 相关
keywords: JVM，jtreg, 调测，选项
---

## 运行时选项

### 纯解释执行

```
-Xint
```

### `PrintCompilation`选项

请参考 [About PrintComiplation](https://link.zhihu.com/?target=https%3A//gist.github.com/rednaxelafx/1165804%23file-notes-md)

### `PrintAssembly`选项

请参考 [PrintAssembly](https://wiki.openjdk.java.net/display/HotSpot/PrintAssembly)

## 编译 JDK

- 构建可调试版本

  ```shell
  bash ./configure --with-debug-level=fastdebug --with-native-debug-symbols=internal
  make images CONF=fastdebug
  ```

## 基本测试

- 在 configure 前指 jtreg

  设置环境变量 JT_HOME 为 jtreg 的安装路径

- 执行测试

  ```shell
  make test TEST="tier1"
  ```

## JVM 字节码

- 字节码指令手册

  [Chapter 6. The Java Virtual Machine Instruction Set](https://docs.oracle.com/javase/specs/jvms/se8/html/jvms-6.html)

## JVM 内存相关选项

- -Xms<xxxk/m/g>
  表示 JVM 初始化时堆的大小。

- -Xmx<xxxk/m/g>
  表示 JVM 堆可以分配到的最大值。

- -Xmn<xxxk/m/g>
  表示 JVM 堆区新生代的大小

## jtreg 选项参考

[jtreg: Command Line Options](http://openjdk.java.net/jtreg/command-help.html)

## 打印JIT生成汇编指令

- 使用hsdis解析机器指令到汇编指令
  `cp ~/share/hsdis/hsdis-aarch64.so ../jdk/build/linux-aarch64-server-fastdebug/images/jdk/lib/server/`
  
- 开启JVM选项打印汇编指令
  `-XX:CompileCommand=print,java/lang/String.equals` or `-XX:+UnlockDiagnosticVMOptions -XX:+PrintAssembly -XX:+PrintOptoAssembly`
