---
title: hexo配置和美化
date: 2019-06-27 14:34:36
categories: hexo搭建博客
comment: true
toc: true
tags: 
  hexo配置
---



本系列是我在学习hexo+GitHub搭建博客时总结的一些心得，哎，一步一个坑！！

第二部分：美化

{% asset_img girl.jpg girl  %}

<!--more-->

# hexo配置和美化

## 1.站点基本配置

```yml
# Site
title: ljhsir's blog
subtitle: 
description: Lif is fantastic~
keywords: Python Django 爬虫
author: ljh
language: zh-CN
timezone: Asia/Hong_Kong
```

## 2.更换主题

可以到[主题网站](<https://hexo.io/themes/>)下载喜欢的主题，保存到项目根目录的theme文件夹下。

```yml
theme: ocean
```

## 3.增加其他页面

列如增加一个关于作者的界面，命令行输入：

```shell
hexo new page about
```

就会在`你的项目路径`\source下面生成一个about文件夹

## 4. 增加一个文章分类

### 1.创建

在项目文件夹启动命令行输入：

```shell
hexo new page categories
```

成功后会提示：

```
INFO  Created: ~/Documents/blog/source/categories/index.md
```

根据上面的路径，找到`index.md`这个文件，打开后默认内容是这样的：

```markdown
---
title: 文章分类
date: 2017-05-27 13:47:40
---
```

添加`type: "categories"`到内容中，添加后是这样的：

```markdown
---
title: 文章分类
date: 2017-05-27 13:47:40
type: "categories"
---
```

### 2、文章添加“categories”属性

打开需要添加分类的文章，为其添加categories属性。下方的`categories: web前端`表示添加这篇文章到“web前端”这个分类。注意：hexo一篇文章只能属于一个分类，也就是说如果在“- web前端”下方添加“-xxx”，hexo不会产生两个分类，而是把分类嵌套（即该文章属于 “- web前端”下的 “-xxx ”分类）。

```markdown
---
title: jQuery对表单的操作及更多应用
date: 2017-05-26 12:12:57
categories: 
- web前端
---
```

## 5.给文章增加标签

### 1 生成“标签”页并添加tpye属性

打开命令行，进入博客所在文件夹。执行命令

```
$ hexo new page tags

```

成功后会提示：

```
INFO  Created: ~/Documents/blog/source/tags/index.md

```

根据上面的路径，找到`index.md`这个文件，打开后默认内容是这样的：

```
---
title: 标签
date: 2017-05-27 14:22:08
---

```

添加`type: "tags"`到内容中，添加后是这样的：

```
---
title: 文章分类
date: 2017-05-27 13:47:40
type: "tags"
---

```

保存并关闭文件。

#### 2 给文章添加“tags”属性

打开需要添加标签的文章，为其添加tags属性。下方的`tags:`下方的`- jQuery` `- 表格`
 `- 表单验证`就是这篇文章的标签了

```
---
title: jQuery对表单的操作及更多应用
date: 2017-05-26 12:12:57
categories: 
- web前端
tags:
- jQuery
- 表格
- 表单验证
---

```

至此，成功给文章添加分类，点击首页的“标签”可以看到该标签下的所有文章。当然，只有添加了`tags: xxx`的文章才会被收录到首页的“标签”中。