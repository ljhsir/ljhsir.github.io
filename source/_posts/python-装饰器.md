---
title: python 装饰器
comment: true
date: 2019-08-03 16:27:14
categories: python
tags: 装饰器
---

# python装饰器

[TOC]

最近在学习flask，学到权限控制部分涉及到装饰器的知识，有点疑惑，所以网上四处搜集整理了一下。

路漫漫其修远兮，吾将上下而求索。

<!--more-->

## 一、简介

在理解装饰器前需要先了解几个概念：

1. python一切皆对象，所有对象都可作为参数传递。
2. 闭包。

**什么是闭包？**

闭包就是**能够读取其他函数内部变量的函数**。例如在javascript中，只有函数内部的子函数才能读取[局部变量](https://baike.baidu.com/item/局部变量/9844788)，所以闭包可以理解成“**定义在一个[函数](https://baike.baidu.com/item/函数/301912)内部的函数**“。在本质上，闭包是将函数内部和函数外部连接起来的桥梁。[百度百科]([https://baike.baidu.com/item/%E9%97%AD%E5%8C%85/10908873?fr=aladdin](https://baike.baidu.com/item/闭包/10908873?fr=aladdin))

可以归纳为以下几点：

1. 闭包是嵌套函数；
2. 内部函数读取外部函数的变量；
3. 外部函数的返回值为内部函数；

类如：

```python
def outer(v):
    def inner():
        print(v)
    return inner

test = outer("Hello World!") 
test()

'''
输出：

>>> test()
Hello World!
'''
```

**那么什么是装饰器？它又有什么作用呢？**

**装饰器：** 装饰器顾名思义就是对一个函数进行装饰，为其添加一些附属功能的同时又不改变被装饰函数的一个函数。

**作用**：主要作用有框架的路由传参（如flask的`app.route('/)`）、权限验证、插入日志、事务处理、缓存等。

## 二、示例

计算一个函数运行的时间

```python
import random, time

# 计算运行时间的装饰器
def run_time(func):
    def wrapper(nums):
        start_time = time.time()
        func(nums)
        end_time = time.time()
        print("{}:ran for {} seconds".format(func.__name__, end_time-start_time))
    return wrapper
 
# 使用冒泡排序
@run_time
def bubble_sort(nums):
    print(nums)
    length = len(nums)
    for i in range(0, length-1):
        for j in range(0, length-1-i):
              if nums[j] > nums[j+1]:
                  nums[j], nums[j+1] = nums[j+1], nums[j]
    print(nums)

l1 = [random.randint(1, 100) for i in range(10)]
bubble_sort(l1)

'''
输出：

[59, 81, 66, 59, 23, 39, 56, 92, 92, 11]
[11, 23, 39, 56, 59, 59, 66, 81, 92, 92]
bubble_sort:ran for 0.06198382377624512 seconds
'''

```

## 三、python内置装饰器

python常用的内置装饰器有：

1. **@classmethod**：经过该装饰器装饰过的方法为类方法，第一个参数必须是clc（默认），只能通过**类名.方法**或**对象名.\__class__.方法**调用。

   ```python
   class A():
       '''基类'''
       @classmethod
       def print_class_name(clc):
           print(clc.__name__)
   
       def print_hi(self):
           print("hi")
   
   a = A()
   
   a.print_hi()
   a.__class__.print_class_name()
   A.print_class_name()
   
   
   '''
   输出：
   
   hi
   A
   A
   '''
   ```

   2. **staticmethod**：该装饰器装饰的方法为静态方法，该方法不需要访问实例属性和类属性，使用**类名.方法**、**对象名.\__class__.方法**或**对象名.\__class__.方法**调用。

   ```python
   class A():
       '''基类'''
       @staticmethod
       def print_hi():
           print("hi")
   
   
   a = A()
   a.print_hi()
   a.__class__.print_hi()
   A.print_hi()
   
   '''
   输出：
   
   hi
   hi
   hi
   '''
   ```

   3. **@property**：该装饰器装饰过的方法可看作一个属性，可直接通过**类名.方法名**调用。

   ```python
   class Person():
       '''基类'''
       __name = None
       
       def __init__(self, name):
           self.__name = name
   
       @property
       def name(self):
           return self.__name
   
       @name.setter 
       def name(self, name):
           self.__name = name
   
   
   p = Person("张三")
   print(p.name)
   p.name = "李四"
   print(p.name)
   
   '''
   输出：
   
   张三
   李四
   '''
   ```

## 四、缺点

1. 装饰器会对原函数的元信息进行修改，如函数的docstring,\__name__,参数列表；

```python
def run_time(func):
    def wrapper():
        func()
    return wrapper

@run_time
def f():
    print("Hello World!")

f()
print(f.__name__)

'''
输出：
Hello World!
wrapper
'''
```

这个问题可以用python内置的一个装饰器wraps来解决，它会将原函数的所有原信息拷贝到装饰器函数中，使得装饰器函数的所有信息和原函数一致。

```python
from functools import wraps
def run_time(func):
    @wraps(func)
    def wrapper():
        func()
    return wrapper

@run_time
def f():
    print("Hello World!")

f()
print(f.__name__)

'''
输出：

f
'''
```

2. 被@staticmethod 和 @classmethod装饰过的函数不能再被装饰。
3. 不要在装饰器外添加逻辑功能。

## 参考

https://www.cnblogs.com/whyaza/p/9505205.html

https://blog.csdn.net/love20165104027/article/details/82934312

https://blog.csdn.net/u010967872/article/details/80329280