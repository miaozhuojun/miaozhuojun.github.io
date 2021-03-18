---
layout: wiki
title: gdb
categories: gdb
description: gdb 使用技巧
keywords: gdb, 技巧
---

### GDB 使用技巧，将不断更新

#### 打印变量

- 打印十六进制数

  ```gdb
  p/x val
  ```

#### 设置断点

- `b func_name`
- `b file_name:line_number`
- `b *address`
