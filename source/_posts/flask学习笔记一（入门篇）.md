---
title: flask学习笔记一（入门篇）
comment: true
date: 2019-08-06 10:50:31
categories: flask
tags:
  web框架
---

## 一、简介

**Flask**是基于python开发的一个基于**MVC**设计模式的、**微**内核的web开发框架。它小巧轻量特别适合于各种小型项目和有意从事python web开发的新手。当然，它应对大型项目也不在话下。

Flask有着丰富的扩展，它本身只依赖两个外部库`jinjia2`模板引擎以及`Werkzeug`WSGI工具集。因此有ORM或者表单之类需求的可以根据需求自己增加扩展。[中文文档](<http://docs.jinkan.org/docs/flask/>)

<!--more-->

## 二、开始Flask项目

### 1、安装

安装了python环境（python2.6或更高版本）并且有pip或者easy_install包管理工具的可以直接在命令行输入：

```shell
pip install flask
```

或

```shell
easy_install flask
```

### 2、最小的flask应用

新建一个python文件（如：hello.py， 不能为flask.py，原因后面再讲），在文件中写入以下代码：

```python
from flask import Flask

app = Flask(__name__)
@app.route("/")
def hello():
    return "Hello World!"

if __name__ == "__main__":
    app.run()
```

然后执行`python hello.py`，在浏览器访问http://127.0.0.1:5000/ 就可以看到 Hello World!，表示你已经完成了一个最简单的Flask应用。

### 3、代码详解

1. `from flask import Flask`在这里从flask包里导入了Flask类， 该类的实例是我们的WSGI（Web Server Gateway Interface Web服务网关接口）应用程序。
2. `app = Flask(__name__)` 这里是创建了一个Flask的实例， Flask的第一个参数必须是你创建的应用模块或者包的名称。所以你应该传入`__name__`。
3. `@app.route("/")`这里是使用了route()装饰器将url和视图函数连接起来，即在什么样的URL下触发哪一个视图函数。如该例中， 我们的地址是127.0.0.1:5000，当在浏览器访问到http://127.0.0.1:5000/ 是就会触发 hello()执行相关操作。
4. `app.run()`这条语句是运行这个应用， `if __name__ == "__main__":`这条语句判断了是这个文件或者包是否是主程序的入口，还是作为一个包导入，类似于c语言的`int main()`。

### 4、调试模式

在上例中我们已经运行起来了这个最小的应用， 但是敲代码粗心的同学可能会发现，要是某个地方出错了，还得把它`ctrl+c`重启服务一下， 这样就很麻烦，不符合python优雅的风格，但是你别担心，Flask完全考虑到了。

你可以在hello.py中启动**调试模式**，这样每次代码保存修改后，可以自动重新载入，而且发生错误时会有相关的信息让你debug。

**方法一：**在应用对象上设置

```python
app.debug = True
app.run()
```

**方法二：**作为参数传递给run()方法

```python
app.run(debug=True)
```

在部署到生产环境上时建议关掉调试模式。

## 后记

刚学完Flask开发一个微电影应用，觉得有些地方不是很清楚，而且写过的有些东西记忆有些模糊了，参考官方文档整理了一下，加油吧。

