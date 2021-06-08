---
layout: wiki
title: shell
categories: shell
description: shell 常用命令使用方法
keywords: shell, 命令行
---

## tar

- 压缩

  `tar zcvf <target>.tar.gz <target>`

- 解压

  `tar zxvf <target>.tar.gz`

这里的选项`z`表示使用 gz 压缩，`c`代表 tar 的打包，`x`代表 tar 的解包，`v`表示打印过程。

## 将户用添加进 sudoers

使用系统命令`visudo`，添加如下配置：

```
username ALL=(ALL:ALL) NOPASSWD:ALL
```

如果`/etc/sudoers`可编辑，也可直接编辑此文件。

## 添加 man 手册

有些环境没有`man`命令，需要安装 man-pages 这个包：

```bash
yum install -y man-pages
```

## 远程登陆 shell

要从其他机器登陆 linux shell，比如 Windows shell，只需要使用`ssh`命令即可：

```bash
ssh <name>@<IP>
```

## 反汇编

`objdump <option> a.out`

-d：将代码段反汇编。

-S：将代码段反汇编的同时，将反汇编代码和源代码交替显示，编译时需要给出 -g，即需要调试信息。

-C：将 C++ 符号名逆向解析。

-l：反汇编代码中插入源代码的文件名和行号。

-j section：仅反汇编指定的 section。可以有多个 -j 参数来选择多个 section。
