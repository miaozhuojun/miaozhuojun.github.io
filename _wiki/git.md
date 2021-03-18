---
layout: wiki
title: git
categories: git
description: git 配置
keywords: git, 配置
---

### .gitconfig 的个人配置，将不断更新

```shell
[user]
        email = mouzhuojun@huawei.com
        name = miaozhuojun
[alias]
        st = status
        br = branch
        co = checkout
        lg = log --graph --pretty=oneline --abbrev-commit
[core]
        editor = vim
[http]
        sslVerify = false
```

### git 操作笔记

#### 修改远程仓库

- 添加远程仓库

  `git remote add repository_name repository_ssh_or_http_address`

- 远程仓库重命名

  `git remote rename old_name new_name`

- 删除远程仓库

  `git remote rm repository_name`

#### 本地文件修改

- 重命名文件

  `git mv old_name new_name`

#### 使用镜像加速 git clone 和 git pull

使用`github.com.cnpmjs.org`替换`github.com`
