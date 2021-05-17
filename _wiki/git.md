---
layout: wiki
title: git
categories: git
description: git 配置
keywords: git, 版本管理
---

## .gitconfig 的个人配置，将不断更新

[mygitconfig](../mygitconfig)

## git 操作笔记

### 修改远程仓库

- 添加远程仓库

  `git remote add repository_name repository_ssh_or_http_address`

- 远程仓库重命名

  `git remote rename old_name new_name`

- 删除远程仓库

  `git remote rm repository_name`

- 修改本地分支和远程仓分支的映射关系

  `git branch -u <repository>/<branch> <branch>`

### 本地文件修改

- 重命名文件

  `git mv old_name new_name`

### 使用镜像加速 git clone 和 git pull

使用`github.com.cnpmjs.org`替换`github.com`

### 制作 patch

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

### 打 patch

  ```shell
  git apply patch_name.patch
  ```

### 查看某次提交

- 查询 commit ID

  ```shell
  git log
  ```

- 根据 commit ID 查看某次提交的具体信息

  - 查看最新提交

    ```shell
    git show
    ```

  - 查看某次提交

    ```shell
    git show commitId
    ```

  - 查看某次提交中某个文件的修改

    ```shell
    git show commitId fileName
    ```

### 从 github 上下载某次 commit 对应的 patch

- 首先获取某次 commit 的 ID
- 然后修改 commit 的 URL

  ```
  http://github/com/foo/bar/commit/${ID}.patch/
  ```

### stash 使用方法

- 保存现场未提交修改

  `git stash`

- 查看保存的修改

  `git stash list`

- 查看某次保存的修改内容

  `git stash show -p <stash>`

- 删除某次保存

  `git stash drop <stash>`

- 恢复保存修改到工作空间

  `git stash pop`

### 删除分支

```
git br -d <branch name>     // 删除已经 merge 的分支
git br -D <branch name>     // 删除还没有 merge 的分支
```

### rebase

合并主干代码时建议使用`rebase`：

```shell
git co <feature>
git rebase <master>
```
