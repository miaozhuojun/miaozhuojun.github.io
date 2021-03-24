---
layout: wiki
title: gdb
categories: gdb
description: gdb 使用技巧
keywords: gdb, 技巧
---

### 打印变量

- 打印十六进制数

  ```shell
  (gdb) p/x val
  ```

### 设置断点

- `b func_name`
- `b file_name:line_number`
- `b *address`

### 修改变量

```shell
(gdb) print x=<num>
```
