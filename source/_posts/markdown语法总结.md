---
title: markdown语法总结
date: 2019-06-28 21:30:00
categories: 学习总结
tags: 
  markdown
---

这里是我在学习过程中总结的markdown语法，来源包括[菜鸟教程](<https://www.runoob.com/>)和我看过的一些视频，但是忘记来源了。喜欢的可以看一下！\^_\^ 

![hand](./markdown语法总结/hand.jpg)

<!--more-->

[TOC]

```markdown
[toc] # 生成目录
```



## 标题

**1. 使用 = 和 \- 标记一级和二级标题  **

```markdown
我是一级标题
==========
我是二级标题
----------

```

**2. 使用\#号标记**

一个\#号克表示一级标题两个\# 可表示二级标题

```mark
# 我是一级标题
## 我是二级标题
### 我是三级标题

```

## 段落格式

Markdown 段落没有特殊的格式，直接编写文字就好，**段落的换行是使用两个以上空格加上回车**。

```mark
这是一个段落   
这是第二段

这是一个段落

这是第二段
```

## 字体

Markdown 可以使用以下几种字体：

```markdown
*斜体文本*
_斜体文本_
**粗体文本**
__粗体文本__
***粗斜体文本***
___粗斜体文本___
```

## 分隔线

可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。也可以在星号或是减号中间插入空格。

```markdown
***

* * *

*****

- - -

----------
```

## 删除线

如果文字要添加删除线，只需要在文字的两端加上两个波浪线 **~~** 即可：

```markdown
~~BAIDU.COM~~
```

## 下划线

下划线可以通过 HTML 的 **<u>** 标签来实现：

```markdown 
<u>带下划线文本</u>
```

## 脚注

脚注是对文本的补充说明，格式如下：

```
[^要注明的文本]
```

**演示：**

百度[^1]

[^1]: 国内最大的搜索引擎

```markdown
百度[^1]
[^1]:国内最大的搜索引擎
```

## 列表

### 无序列表

- 无序列表
- 无序列表
- 无序列表
- +-*三种符号都可以

### 有序列表

1. 有序列表
2. 有序列表
3. 有序列表
4. 数字加点就可以

```markdown
### 无序列表
* 无序列表
+ 无序列表
- 无序列表
* +-*三种符号都可以

### 有序列表
1. 有序列表
1. 有序列表
1. 有序列表
1. 数字加点就可以
```

### 嵌套列表

各级之间符号不同，相隔四个空格，typora快速插入表格 `CTRL+t`：

- 云南
  - 昆明
    - 嵩明
    - ...
  - 昭通
    - 巧家
    - ...
  - ...
- 四川
  - 攀枝花
  - 不知道

```markdown
* 云南
    + 昆明
        - 嵩明
        - ...
    + 昭通
        - 巧家
        - ...
    + ...
* 四川
    - 攀枝花
    - 不知道
```

## markdown区块

Markdown 区块引用是在段落开头使用 **>** 符号 ，然后后面紧跟一个**空格**符号：

```markdown
> 区块引用
> 菜鸟教程
> 学的不仅是技术更是梦想
```

__演示：__

> 区块引用
> 菜鸟教程
> 学的不仅是技术更是梦想

### 区块的嵌套

另外区块是可以嵌套的，一个 **>** 符号是最外层，两个 **>** 符号是第一层嵌套，以此类推退：

```markdown
> 最外层
> > 第一层嵌套
> > > 第二层嵌套
```

> 最外层
>
> > 第一层嵌套
> >
> > > 第二层嵌套

### 区块中使用列表

区块中使用列表实例如下：

```
> 区块中使用列表
> 1. 第一项
> 2. 第二项
> + 第一项
> + 第二项
> + 第三项
```

显示结果如下：

> 区块中使用列表
>
> 1. 第一项
> 2. 第二项
>
> - 第一项
> - 第二项
> - 第三项

### 列表中使用区块

如果要在列表项目内放进区块，那么就需要在 **>** 前添加四个空格的缩进。

区块中使用列表实例如下：

```markdown
* 第一项
    > 第一一
    > 第二二
* 第二项
```

显示结果如下：

- 第一项

  > 第一一
  > 第二二

- 第二项

## markdown代码 

如果是段落上的一个函数或片段的代码可以用反引号把它包起来（**`**），例如：

```markdown
`printf()` 函数
```

显示结果如下：

`printf()` 函数

### 代码区块

代码区块使用 **4 个空格**或者一个**制表符（Tab 键）**或者```` `包裹一段代码并指定一种语言（好像空格和制表符不支持个人推荐用 最后一种）。

```markdown
$(document).ready(function () {
alert('RUNOOB');
```

~~~markdown
```javascript
$(document).ready(function () {
    alert('RUNOOB');
});
```
~~~

实例如下：

```javascript
$(document).ready(function () {
    alert('RUNOOB');
});
```

## 链接

链接使用方法如下：

链接使用方法如下：

```markdown
[链接名称](链接地址)

或者

<链接地址>
```

示例如下：

[百度](https://www.baidu.com)

或者

<https://www.baidu.com>

### 高级链接

```markdown
链接也可以用变量来代替，文档末尾附带变量地址：
这个链接用 1 作为网址变量 [Google][1]
这个链接用 runoob 作为网址变量 [Baidu][baidu]
然后在文档的结尾为变量赋值（网址）

  [1]: http://www.google.com/
  [baidu]: http://www.baidu.com/
```

[Google][1]
 [Baidu][baidu]

[1]: http://www.google.com/
[baidu]: http://www.baidu.com/

## 图片

Markdown 图片语法格式如下（菜鸟教程为例）：

```markdown
![alt 属性文本](图片地址)

![alt 属性文本](图片地址 "可选标题")

高级：
这个链接用 1 作为网址变量 [RUNOOB][1]
然后在文档的结尾位变量赋值（网址）

[1]: http://static.runoob.com/images/runoob-logo.png
```



![RUNOOB 图标](http://static.runoob.com/images/runoob-logo.png"RUNOOB")

**高级链接展示：**

![高级链接][2]

[2]: http://static.runoob.com/images/runoob-logo.png



Markdown 还没有办法指定图片的高度与宽度，如果你需要的话，你可以使用普通的 <img> 标签。

```html
<img src="http://static.runoob.com/images/runoob-logo.png" width="50%">
```

<img src="http://static.runoob.com/images/runoob-logo.png" width="50%">



## 表格

Markdown 制作表格使用 **|** 来分隔不同的单元格，使用 **-** 来分隔表头和其他行。

语法格式如下：

```markdown
|  表头   | 表头  |
|  ----  | ----  |
| 单元格  | 单元格 |
| 单元格  | 单元格 |
```

**示例:**

| 表头   | 表头   |
| ------ | ------ |
| 单元格 | 单元格 |
| 单元格 | 单元格 |

**我们可以设置表格的对齐方式：**

- **-:** 设置内容和标题栏居右对齐。
- **:-** 设置内容和标题栏居左对齐。
- **:-:** 设置内容和标题栏居中对齐。    

**示例:**

| 左对齐 | 右对齐 | 居中对齐 |
| :----- | -----: | :------: |
| 单元格 | 单元格 |  单元格  |
| 单元格 | 单元格 |  单元格  |

## 着重显示

`重点`

```markdown
`重点`
```

## 添加表情

: kissing;
:+表情名;

## 脚注

## Markdown 高级技巧

### 支持的 HTML 元素

不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。

目前支持的 HTML 元素有：`<kdb> <b> <i> <em> <sup> <sub> <br>`等 ，如：

```markdown
使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑
```

### 转义

Markdown 使用了很多特殊符号来表示特定的意义，如果需要显示特定的符号则需要使用转义字符，Markdown 使用反斜杠转义特殊字符：

```markdown
**文本加粗** 
\*\* 正常显示星号 \*\*
```

### 公式

当你需要在编辑器中插入数学公式时，可以使用两个美元符 $$ 包裹 TeX 或 LaTeX 格式的数学公式来实现。提交后，问答和文章页会根据需要加载 Mathjax 对数学公式进行渲染。如：

```
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$tep1}{\style{visibility:hidden}{(x+1)(x+1)}}
$$
```

输出结果为：
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$