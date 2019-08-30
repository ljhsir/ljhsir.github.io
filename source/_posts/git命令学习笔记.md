---
title: git命令学习笔记
comment: true
date: 2019-08-30 10:54:19
categories: git
tags:
	git
	笔记
---

# git命令

## 一、简介

Git是一个分布式版本控制工具（各种后悔药）。

## 二、初始化(init)

在指定目录下执行`git init`;

`git init myrepo`会创建一个myrepo的文件夹并在该文件夹下初始化；

初始化后会生成一个`.git`的隐藏目录，就是本地仓库；

## 三、状态（status）、提交(commit)、回退(checkout)

==modified （已修改）-> staged（已暂存） -> committed（已提交） ->remote repo（远程仓库）==

1、`git status` 查看暂停区状态， 未添加的更改（文件）为红色；

2、`git add .`将当前目录下所有更改的文件添加到暂停区，添加的变为绿色；

3、`git commit -m "massage"` 将暂停区的更改提交到工作区，-m指令可以添加信息；（造了一个后悔药）会返回一串信息：分支+id前七位+massage；

4、`git checkout id`回退到某个版本（某一次提交）的状态；

5、`git log` 查看提交的日志；

​	按**q**退出；

​	==-p==参数可以查看具体更改的内容；

​	==--oneline==简略信息只显示一行；

​	==--all==显示全部日志，j往前，k往后；

​	==--graph==图像化显示；（字符化的）

## 四、标签（tag）

相当于某一次提交很重要，你给它命名；

在某次commit满意后可以用`git tag -a tagname -m "massage"`, 默认是最近的commit；可以在命令最后添加id，指定某一次提交加标签；

## 五、分支（branch）

1、`git branch branchName`创建分支；

2、`git checkout branchName`切换分支；

## 六、合并分支

1、`git checkout -b branchName`创建并切换分支；

2、`git merge branchName`合并分支；

有冲突的情况

```
<<<<<<<<HEAD
主分支的内容

======（分割两个分支的内容）
其他分支的内容

>>>>>>OtherBranch
```

## 七、远程仓库

`git remote`打印出所有远程仓库，==-v==显示详细信息；

1、`git remote add remoteNmae remoteURL`添加远程仓库；

```shell
git remote add github http://github.com/ljhsir
```

remoteName远程名是我们自己定义的，如果不加remoteName默认为origin；

2、`git push -u remoteName branchName`上传代码；

```shell
git push -u github master
```

## 八、多人合作

1、`git clone remoteURL` 将远程仓库克隆到本地；后面可以加一个目录名，如果不加默认为项目名；

2、`git pull`从远程仓库拉取更新； 

3、多人合作在修改同一块内容遇到rejected（驳回），可以先pull然后修改再push；

4、`git pull` = `git fetch`+`git merge`先抓取再合并；

___
**后记**
入门前端的小伙伴们可以去看看[大表哥](https://biaoyansu.com/)的课程，我很喜欢的。学习了很多。继续加油！！



