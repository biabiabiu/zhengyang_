---
title: "LOOKUP提取字符串首部数值"
description:  "Excel中用LOOKUP提取字符串首部数值"
date: 2022-02-11T20:22:17+08:00
draft: false

tags: ["Excel","Lookup"]
categories: ["Excel"]
---



Excel中使用`LOOKUP`提取字符串首部数值。

<!--more-->

如果要提取下面一串内容中首部的数字，要如何操作？

`99.9千克的狗熊最可爱`

&nbsp;

#### 具体操作

##### 分列

<center>
    {{<image src="/images/gif/excel_lookup_example1.gif" title="分列操作" width="400px" >}}
</center>


但是分列在大量数据格式不对称的情况下就失灵了

&nbsp;

##### 公式

<center>
    {{<image src="/images/gif/excel_lookup_example2.gif" title="公式操作" width="400px" >}}
</center>


公式的效果更好一些

&nbsp;

#### 解释

##### ROW($1:$4)

<center>
    {{<image src="/images/gif/excel_row_example1.gif" title="公式ROW" width="400px" >}}
</center>


这个公式会生成一个常量数组` {1;2;3;4}`，编辑栏会有变化

目的是为了方便LEFT在D2单元格中取值，为什么会是`$1:$4？`

&nbsp;

##### -LEFT(D2,ROW($1:$4))

<center>
    {{<image src="/images/gif/excel_left_example1.gif" title="公式LEFT" width="400px" >}}
</center>



LEFT配合上ROW生成的常量数组，会分别取左边的前一个、前两个、前三个、前四个字符

加负号的目的，是对其进行减负运算，数值、文本型数值就直接变成0或负值，其他的不能转的就会变成错误值，最后即 `{-9;-99;-99;-99.9}`

这就是ROW的作用，当然这里用`ROW($1:$3)`也可以，而为什么是四个，因为要提取的这些内容中包含数字最多是四位 即6400

&nbsp;

##### LOOKUP(1,-LEFT(D2,ROW($1:$4)))

即

```
LOOKUP(1,{-9;-99;-99;-99.9})
```

[LOOKUP](https://support.microsoft.com/zh-cn/office/lookup-%e5%87%bd%e6%95%b0-446d94af-663b-451d-8251-369d5e3864cb?ui=zh-cn&rs=zh-cn&ad=cn)有这些特点：

- LOOKUP函数会忽略错误值
- 如果LOOKUP找不到要找的值，最终匹配小于或等于它的最大值(在以升序排列情况下)

没有排序的话，LOOKUP则总会认为后边的数字比前边的大，所以最终会认为最后的值是最大的，所以最后会匹配到最完整的带负号的数值

最后再将匹配到的数值做减负运算，就是我们想要的值，即

```
LOOKUP(1,-LEFT(D2,ROW($1:$4)))
-LOOKUP(1,{-9;-99;-99;-99.9})
```

