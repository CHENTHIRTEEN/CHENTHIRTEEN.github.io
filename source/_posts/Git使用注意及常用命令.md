---
title: Git使用注意及常用命令
date: 2021-01-26 16:11:29
index_img: /img/git_logo.png
categories:
- Git
tags:
- 开发工具
- 学习笔记
---
# Git使用注意及常用命令

## git设置用户信息

```shell
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

***不带后缀的命令可以查看本机用户信息***

---

+ 将目录变为Git可管理的仓库

``` shell
$ git init
```

## 将文件添加到版本库

+ 将文件添加到仓库

``` shell
$ git add filename
```

+ 将文件提交到仓库

``` shell
$ git commit -m "提交备注，为了代码规范必填"
```

+ git命令必须在git仓库内执行
+ 注意添加文件时文件是否存在

---

## 时光机穿梭

+ git status命令可以查看仓库当前状态

``` shell
10303@DESKTOP-9B9NUVT MINGW64 /d/myHub/OnlineJudge (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.md

no changes added to commit (use "git add" and/or "git commit -a")

```

+ 查看文件具体被修改的内容

**git diff "filename"**

``` shell
$ git diff "readme.md"
diff --git a/readme.md b/readme.md
index c8a8781..699d945 100644
--- a/readme.md
+++ b/readme.md
@@ -1,2 +1,7 @@
 # 记录本人不定期的OJ刷题记录

+##### 目前已有
+
++ LuoGu
++ AcWing
++ PTA
\ No newline at end of file

```

---

#### 版本回退

+ 查看历史纪录

``` shell
$ git log
commit bbedeb9a6cced4d2ec9449525af3d1d487e5eedf (HEAD -> master)
Author: CHENTHIRTEEN <1030339437@qq.com>
Date:   Tue Jan 26 13:06:06 2021 +0800

    add som distributed

commit 7d599a92c034fed30e7c75539503189a19e269ec
Author: CHENTHIRTEEN <1030339437@qq.com>
Date:   Tue Jan 26 13:03:44 2021 +0800

    add som distributed

commit c71a269f75f080bfd168ea2e14c586d6a93e49f6
Author: CHENTHIRTEEN <1030339437@qq.com>
Date:   Tue Jan 26 12:39:36 2021 +0800

    add a readme file

```

<font color="red">git log</font>从最近到最远显示提交日志

+ 带--pretty=oneline参数

``` shell
$ git log --pretty=oneline
bbedeb9a6cced4d2ec9449525af3d1d487e5eedf (HEAD -> master) add som distributed
7d599a92c034fed30e7c75539503189a19e269ec add som distributed
c71a269f75f080bfd168ea2e14c586d6a93e49f6 add a readme file

```

+ **git中HEAD表示当前版本上个版本为HEAD^N个版本为HEAD~N**

+ 回退命令

``` shell
$ git reset --hard HEAD~2
HEAD is now at c71a269 add a readme file
```

+ 回退后再次使用git log

```  shell
$ git log
commit c71a269f75f080bfd168ea2e14c586d6a93e49f6 (HEAD -> master)
Author: CHENTHIRTEEN <1030339437@qq.com>
Date:   Tue Jan 26 12:39:36 2021 +0800

    add a readme file
```

+ 窗口未关闭可以使用commit id回到某个版本

``` shell
$ git reset --hard bbedeb
```

commit id取前几位即可

+ 若关闭了窗口可以通过git reflog查看记录的每一次命令

``` shell
$ git reflog
c71a269 (HEAD -> master) HEAD@{0}: reset: moving to HEAD~2
bbedeb9 HEAD@{1}: commit: add som distributed
7d599a9 HEAD@{2}: commit: add som distributed
c71a269 (HEAD -> master) HEAD@{3}: commit (initial): add a readme file
```

