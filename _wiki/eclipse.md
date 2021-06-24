---
layout: wiki
title: eclipse
categories: eclipse
description: eclipse 使用技巧
keywords: eclipse，配置
---

以下是关于 eclipse 的使用小技巧，会不断更新

## 搜索文件

`ctrl+shift+r`

## 如何跳转到 Java 系统类的源代码

点 window -> Preferences -> Java -> Installed JRES 配置对应 JDK 源码编译出的 JRE 即可，它会自动配置 Source Attachment。

## 搜索符号

`Ctrl+Shift+t`

## 性能提升

- 禁止自动 build

  eclipse 默认是自动编译的，自动编译会消耗系统资源，如果你想取消自动编译，可以在eclipse的菜单栏中点击project，去掉build automaticaly前面的勾。
  
## 分屏显示同一文件

某个文件很大，可能有数千行，当你想要参考文件中的某一部分来添加内容时分屏显示将格外方便，分屏的方法如下: 

Window -> Editor -> Toggle Split Editor (Ctrl + _)

关闭分屏只要再次同样操作即可。
