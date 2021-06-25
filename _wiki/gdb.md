---
layout: wiki
title: gdb
categories: gdb
description: gdb 使用技巧
keywords: gdb, 技巧
---

## 打印变量

- 打印十六进制数

  ```shell
  (gdb) p/x val
  ```

## 设置断点

- `b func_name`
- `b file_name:line_number`
- `b *address`

## 修改变量

```shell
(gdb) print x=<num>
```

## 单步调试

通常情况下，step 命令和 next 命令的功能相同，都是单步执行程序。不同之处在于，当 step 命令所执行的代码行中包含函数时，会进入该函数内部，并在函数第一行代码处停止执行。

查看汇编，并单步：

```shell
display /10i $pc
si/ni
```

## 处理信号

在调试JVM时，由于JVM对某些信号会做处理，所以不能让GDB先处理，需要屏蔽：

```shell
handle SIGSEGV pass nostop noprint
handle SIGILL pass nostop noprint
```

## 调试 coredump

```shell
gdb path/to/the/executable path/to/the/coredump
```

## 退出当前函数

- 第一种用`finish`命令，这样函数会继续执行完，并且打印返回值，然后等待输入接下来的命令。

- 第二种用`return`命令，这样函数不会继续执行下面的语句，而是直接返回。也可以用`return expression`命令指定函数的返回值。
