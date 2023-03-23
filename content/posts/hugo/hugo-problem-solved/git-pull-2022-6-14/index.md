---
title: "博客出了问题"
description:  "这篇内容记录了我是如何解决由于不小心删掉某些文件后Git无法正常使用的问题。"
keywords: ["Github","git","Hugo"]

date: 2022-06-14T11:04:42+08:00
draft: false

tags: ["Hugo","Git"]
categories: ["Hugo"]
---

博客长时间未进行维护更新后发生了点小意外，这里记录了该问题的解决过程。

<!--more-->

由于这段时间工作比较忙，一直没有精力来更新维护我的博客，落下一段时间后再拿起使用时就遇到了问题

首先是路径下`git bash here`后敲`hugo`没有了反应，后面发现hugo的程序文件不知何时被删除了，原来它在`D:\Hugo\bin`下。重新补上后显示`command not found`，好家伙，环境变量也被清理了，只好再给加上

本以为意外到这里就结束了，在完成一篇后准备push，又提示`git command not found`，顿时无语

直接从头再来

1. 先将Git重装了一遍

2. 拉取远程文件代码

   ```bash
   git https://github.com/biabiabiu/zhengyang_.git
   ...
   ```

3. 查看当前分支情况

   ```bash
   $ git branch -al
   * master
     remotes/origin/HEAD -> origin/master
     remotes/origin/master
   ```

4. 将本地分支与远程关联同步

   ```bash
   $ git pull origin master
   From https://github.com/biabiabiu/zhengyang_
    * branch            master     -> FETCH_HEAD
   Already up to date.
   ```

5. 查看是否关联成功

   ```bash
   $ git remote -v
   origin  https://github.com/biabiabiu/zhengyang_.git (fetch)
   origin  https://github.com/biabiabiu/zhengyang_.git (push)
   ```

6. git push

   添加一个`git_test.txt`文件

   ```bash
   git add .
   git commit -m "git-test"
   git push
   ```

   可以看到`git_test.txt`文件

   <center>
       <img class="jf-image-shadow" src="/images/still-image/2022-06-14-1.png" title="git push success" height="100%" width="80%"/>
   </center>

