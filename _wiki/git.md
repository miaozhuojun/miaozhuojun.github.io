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

#### 制作 patch

- 如果修改尚未提交

  ```shell
  git diff > patch_name.patch
  ```

- 如果修改有新增文件，且新增文件不在 git 管理内

  ```shell
  git diff --cached > patch_name.patch
  ```

- 如果修改中还包含二进制文件，例如图片

  ```shell
  git diff --cached --binary > patch_name.patch
  ```

- 以某次提交内容制作 patch

  ```shell
  git format-patch -1 commit_id
  ```

  这里的 1 代表生成从 commit_id 起往前 1 个提交对应的 patch，也可以生成多个提交对应的 patch

#### 打 patch

  ```shell
  git apply patch_name.patch
  ```
