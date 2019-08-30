---
title: Flask学习笔记二（路由与HTTP请求篇）
comment: true
date: 2019-08-09 16:01:23
categories: flask
tags:
  路由
  HTTP
---

## 一、路由

### 1、什么是路由？

在[入门篇](<https://www.jianshu.com/p/26b7b222d326>)中我们已经实现了一个最小的Flask应用，当我们访问到http://127.0.0.1:5000/ 时页面就会显示出我们在`hello()`返回的“Hello World！”。像在这个应用中的`route("/")`装饰器将一个方法绑定到某一个指定的URL上就叫做**路由**。

<!--more-->

### 2、路由变量规则

在URL中可以添加变量，`<variable_name>`标记变量的名字， 可以作为命名参数传递到视图函数中使用。可根据规则`<converter:variable_name>`来指定一个可选的转换器。如：

```python
@app.route("/<name>/")
def print_name(name):
    return "名字是：%s" % name

@app.route("/<int:age>/")
def print_age(age):
    return "年龄是：%d" % age

@app.route("/<float:height>/")
def print_height(height):
    return "身高是：%s" % height
```

支持的转换器有：

| 数据类型 |                            |
| :------: | -------------------------- |
|   int    | 整型变量                   |
|  float   | 整型或浮点型变量           |
|   path   | 和默认的相似，但也接受斜线 |

**规范的URL在末尾带有”/“**。如：

```python
app.route("/home/")
def hello():
    return "in home!"

app.route("/outside")
def hello():
    return "outside!"
```

如果在浏览器中输入”http://127.0.0.1:5000/home“或者”http://127.0.0.1:5000/home/“你都可以看到输出”in home！“；

当在浏览器中输入”http://127.0.0.1:5000/outside“你可以看到”outside“，但是输入”http://127.0.0.1:5000/outside/“你可能就会看到”404“；

### 3、构造URL

`url_for()`方法可以构造一个url。该方法的第一个参数是`str`类型，是一个试图函数名， 后面可添加在url中声名的命名参数，或者get请求的其他参数。

```python
from flask import url_for

@app.route("/hello/")
def hello(height):
    return "hello"

@app.route("/yourname/<name>/")
def print_name(name):
    return "名字是：%s" % name

@app.route("/yourage/")
def print_age():
    return "年龄是：%s" % request.args.get("age", "18")

print(url_for('hello'))
print(url_for('print_name', name="Mike"))
print(utl_for('print_age', age=20))

```

**优点**：

1. 描述性好，修改方便；
2. 转义特殊字符和Unicode数据；
3. 方便处理复杂的路由关系；

## 二、HTTP方法

HTTP方法（"谓词"），常见的有：

- **GET**：获取页面信息，通过`?参数名=值&参数名=值...`传递数据；
- **POST**：通常是html通过表单给服务器传数据的方法；
- **HEAD**：获取消息头；
- **PUT**：与POST类似，但是服务器可能触发了存储过程多次，多次覆盖掉旧值。
- **DELETE**：删除给定位置的信息；
- **OPTIONS**：给客户端提供一个敏捷的途径来弄清这个 URL 支持哪些 HTTP 方法。

可以在`route('/',methods=[])`methods中指定允许的请求方法。默认为“GET”方法。

```python
@app.route('/', methods=["GET", "POST"])
def hello():
    pass
```



## 后记

继续整理，如有错误之处还请多多指教！(oﾟvﾟ)ノ