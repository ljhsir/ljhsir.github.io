---
title: hexo+github搭建个人博客
comment: true
date: 2019-08-01 14:19:30
categories: hexo
tags:
  个人博客
---

本文将介绍的是如何使用`hexo`与`GitHub`搭建一个免费的个人博客，作为学生党和爱好写作人士这篇博文一定会让你有所得，本博客也是基于hexo和GitHub搭建而成，欢迎各位访问。

<!--more-->

[TOC]



## 一、简介

**Hexo**

hexo是基于node.js编写而成的一个快速、简洁的静态web框架，该框架使用Markdown解析文章，可以快速生成美观的静态网页。有不了解Markdown语法的同学可以看一下我的这篇博客[《Markdown语法总结》](1)。

[hexo官方文档](<https://hexo.io/zh-cn/docs/>)



**Github**

 GitHub是一个面向[开源](https://baike.baidu.com/item/开源/20720669)及私有[软件](https://baike.baidu.com/item/软件/12053)项目的托管平台，因为只支持git 作为唯一的版本库格式进行托管，故名GitHub。[Github](<https://baike.baidu.com/item/GitHub/10145341>)



## 二、搭建环境

由于博主目前经济拮据买不起某果的产品，所以在这里只介绍在Windows10以及Ubantu16.04下的环境搭建。

### 1. 安装Git

**Git** 是一个开源的分布式版本控制系统。[Git](<https://baike.baidu.com/item/GIT/12647237>)

**安装**（高手可自行配置）

- **Windows:** 直接下载Git安装程序，一路下一步默认安装即可 。[Git官网](<https://nodejs.org/en/>)

- **Ubantu：** 命令行输入`sudo apt-get install git`

### 2. 安装Node.js

hexo是由node.js编写而成的，所以这里需要安装一下node.js。这里hexo需要版本最低为6.9。

**安装**（高手可自行配置）

- **Windows:** 直接下载Git安装程序，一路下一步默认安装即可 。[node.js官网](<https://nodejs.org/en/>)

- **Ubantu：** 命令行输入:`sudo apt-get install node.js`

### 3. 创建GitHub个人仓库

首先，登录到[Github](<https://github.com/>)（如果没有账号的请先注册一个），然后创建一个个人仓库，仓库名必须是：`你的用户名.github.io`，正如本网站的`jhsir.github.io`。

### 4. 生成并添加密钥到GitHub

**生成ssh**

只有在添加过密钥后，我们的主机才可以远程操作Github中的仓库。

**Windows** 在你选定的目录下打开git bash，**Ubantu**打开终端，输入：

```shell
git config --global user.name "yourname"
git config --global user.email "youremail"
```

可以用以下命令检查是否配置正确：

```shell
git config user.name
git cinfig user.email
```

然后用下面的命令来生成ssh：

```shell
ssh-keygen -t rsa -C "youremail"
```

接下来找到id_rsa.pub文件，我使用的是Windows10，文件路径是：`C:\Users\ljh\\.ssh`（仅供参考）。



**将ssh添加到GitHub**

1. 登陆到Github，点击你的头像选择`settings`选项
2. 选择`SSH and GPG keys`
3. 点击`New SSH key`创建
4. 填写title，并将id_rsa.pub的内容复制到key里面，提交。

### 5. 安装hexo

命令行输入：

```shell
npm install -g hexo-cli
```

在使用Git进行提交的还需要安装`hexo-deployer-git`，命令行输入：

```shell
npm install --save hexo-deployer-git
```

## 三、 hexo搭建个人博客



### 1. 初始化项目

选择或创建一个空目录，在该目录下输入以下命令进行hexo的初始化，创建配置的文件：

```shell
hexo init
npm install
```

### 2. 目录结构

* **.deploy_git** ：该目录下是要提交到你的GitHub仓库的静态页面的目录
* **node_models**：该目录下是hexo需要的依赖
* **public**：该目录下是渲染好的静态页面的目录
* **scaffolds**：该目录下是模板文件
* **source**：该目录下是你创建的博文的markdown源文件
* **themes**：该目录下是你需要的主题文件
* **_config.yml**：该文件是对整个hexo博客的配置文件

### 3. 配置

打开`_config.yml`文件进行如下简单配置（以本站为例）：

* \# Site

  title: 网站标题（ljhsir's blog）

  subtitle:  网站标题

  description: 描述（Life is fantastic~）

  keywords: 关键词（Python Django 爬虫）

  author: 作则（晓月残风）

  language:  语言（zh-CN）

  timezone: 时区

* \# URL

  url: （网站链接）https://ljhsir.github.io

  root: （根）/

  permalink: 生成的页面的链接格式，如/2019/6/6/测试/（ :year/:month/:day/:title/）

  permalink_defaults: 上一选项的默认

* \# Directory（这里是项目各个文件归类的目录配置）

  source_dir: source

  public_dir: public

  tag_dir: tags

  archive_dir: archives

  category_dir: categories

  code_dir: downloads/code

  i18n_dir: :lang

  skip_render:

* \# Deployment #部署

deploy:

  type: git （上传工具）

  repo:  （上传的仓库）

​    github: https://github.com/ljhsir/ljhsir.github.io.git

​    coding: https://dev.tencent.com/u/ljhsir/p/ljhsir.coding.me/git （这里是我在coding上部署的，没有块需求的可以不用写）

  branch: master（上传的分支）

### 4. 撰写及发布博客

#### 1. 创建文章

在你的项目目录下打开命令行执行：

```shell
hexo new "文章标题"
```

就会在`source/_post`下创建一个`文章标题.md`的文件，你就可以在该文件里面进行创作了。

#### 2. 生成静态网页

在你的项目目录下打开命令行执行：

```shell
hexo generate 
```

或者：

```shell
hexo g
```

就会在`public`下生成静态页面。

#### 3. 本地预览

在你的项目目录下打开命令行执行：

```shell
hexo server
```

你就可以在本地的浏览器打开http:127.0.0.1:4000或者http:localhost:4000进行预览，如果不满意可以继续更改。

#### 4. 发布博客

在你的项目目录下打开命令行执行：

```shell
hexo deploy
```

或者：

```shell
hexo d
```

就可以将静态网站发布到GitHub，部分在发布时可能需要GitHub的登录密码。然后你就可以在浏览器输入你的url查看了。

___

## 后记

由于我也是刚部署完这个，可能在博文中还有些错误或者不足，希望和大家多多交流。QQ群：691070890