---
title: "Python学习-Day02"
description:  "这里记录了我学习python的过程"
keywords: ["python","学习"]

date: 2022-03-01T01:19:10+08:00
draft: false

tags: ["Python"]
categories: ["Python"]
---

Python学习的第二篇日志。

<!--more-->

#### Python学习-Day02

今天学习了第六章的数据类型(二)中的内容，涉及到`列表list`和`元组tuple`一些方法的简单使用

```python
# -------------------------------------
# list练习题
# -------------------------------------
# 1.写代码，有如下列表，按照要求实现每一个功能
li = ["alex", "WuSir", "ritian", "barry", "wenzhou"]
# 计算列表的长度并输出
print(len(li))
# 请通过步长获取索引为偶数的所有值，并打印出获取后的列表
print(li[0::2])
# 列表中追加元素”seven”,并输出添加后的列表
li.append("sever")
print(li)
# 请在列表的第1个位置插入元素”Tony”,并输出添加后的列表
li.insert(0, "Tony")
# 请修改列表第2个位置的元素为”Kelly”,并输出修改后的列表
li[1] = "Kelly"
print(li)
# 请将列表的第3个位置的值改成 “太白”，并输出修改后的列表
li[2] = "太白"
print(li)
# 请将列表l2=[1,”a”,3,4,”heart”]的每一个元素追加到列表li中
l2 = [1, 'a', 3, 4, 'heart']
li.extend(l2)
print(li)
# 请将字符串s=“qwert”的每一个元素添加到列表li中
# 一行代码实现，不允许循环添加
print(li.extend(list('qwert')), li)
# 请删除列表中的元素”ritian”,并输出添加后的列表
print(li.remove('ritian'), li)
# 请删除列表中的第2个元素，并输出删除元素后的列表
print("删除了%s" % li.pop(1), li)
# 请删除列表中的第2至第4个元素，并输出删除元素后的列表
del li[1:4]
print(li)

# -------------------------------------
# 2.写代码，有如下列表，利用切片实现每一个功能
li = [1, 3, 2, "a", 4, "b", 5, "c"]
# 通过对li列表的切片形成新的列表 [1,3,2]
print(li[0:3])
# 通过对li列表的切片形成新的列表 [“a”,4,”b”]
print(li[3:6])
# 通过对li列表的切片形成新的列表 [1,2,4,5]
print(li[0:-1:2])
# 通过对li列表的切片形成新的列表 [3,”a”,”b”]
print(li[1:-2:2])
# 通过对li列表的切片形成新的列表 [3,”a”,”b”,”c”]
print(li[1::2])
# 通过对li列表的切片形成新的列表 [“c”]
print(li[-1])
# 通过对li列表的切片形成新的列表 [“b”,”a”,3]
print(li[-3::-2])

# -------------------------------------
# 3.写代码，有如下列表，按照要求实现每一个功能
lis = [2, 3, "k", ["qwe", 20, ["k1", ["tt", 3, "1"]], 89], "ab", "adv"]
# 将列表lis中的”k”变成大写，并打印列表
lis[2] = 'K'
lis[3][2][0] = "K1"
print(lis)
# 将列表中的数字3变成字符串”100”
lis[1] = 100
lis[3][2][1][1] = 100
print(lis)
# 将列表中的字符串”tt”变成数字 101
lis[3][2][1][0] = 101
print(lis)
# 在 “qwe”前面插入字符串：”火车头”
lis[3].insert(0, '火车头')
print(lis)

# -------------------------------------
# 4. 请用代码实现循环输出元素的索引和值：users = [“武沛齐”,”景女神”,”肖大侠”]
users = ['哈哈哈', '呼呼呼', '啊啊啊']
for item in users:
    print(users.index(item), item)

# -------------------------------------
# 5.有变量 googs = [‘汽车’,’飞机’,’火箭’] 提示用户可供选择的商品
# 用户输入索引后，将指定商品的内容拼接打印，如：用户输入0，则打印 您选择的商品是汽车
googs = ['汽车', '飞机', '火箭']
input1 = input("\n0 汽车"
               "\n1 飞机"
               "\n2 火箭"
               "\n请选择：")
print("您选择了%s" % googs[int(input1)])

# -------------------------------------
# 6.请用代码实现  li = "alex"
# 利用下划线将列表的每一个元素拼接成字符串”a_l_e_x”
str1 = "alex"
li = []
index = 0
while True:
    li.append(str1[index]+'_')
    index += 1
    if str1[index] == 'x':
        li.append(str1[index])
        break
print("".join(li))
# 或直接
print("_".join(list(str1)))

# -------------------------------------
# 7.利用for循环和range找出 0 ~ 100 以内所有的偶数，并追加到一个列表。
l = []
for num in range(101):
    l.append(num)
print(l)

# -------------------------------------
# 8.利用for循环和range 找出 0 ~ 50 以内能被3整除的数，并追加到一个列表。
l = []
for i in range(51):
    if i % 3 == 0 and i != 0:
        l.append(i)
print(l)

# -------------------------------------
# 9.利用for循环和range 找出 0 ~ 50 以内能被3整除的数
# 并插入到列表的第0个索引位置，最终结果如下：
l = []
for i in range(51):
    if i % 3 == 0 and i != 0:
        l.insert(0, i)
print(l)

# -------------------------------------
# 10.查找列表li中的元素，移除每个元素的空格，并找出以”a”开头
# 并添加到一个新列表中,最后循环打印这个新列表。
li = ["alexC", "AbC ", "egon", " riTiAn", "WuSir", "  aqc"]
li_new = []
for item in li:
    if item.strip()[0] == 'a':
        li_new.insert(1, item.strip())
print(li_new)

# -------------------------------------
# tuple练习题
# -------------------------------------
# 1. 比较值 v1 = (1) 和 v2 = 1 和 v3 = (1,) 有什么区别？
# v1为<class 'int'>；v2为<class 'int'>；v3为<class 'tuple'>
# 2. 比较值 v1 = ((1),(2),(3)) 和 v2 = ((1,),(2,),(3,),) 有什么区别？
# v1为(1, 2, 3)；v2为((1,), (2,), (3,))

# -------------------------------------
# 知识点 range
# 在Python2中range会直接生成列表；在Python3中range生成是一个range对象
# 即不会立即在内存中创建这些数，而是在循环时候边使用边创建，节省内存开销
v1 = range(1, 6)   # 生成的数为：[1、2、3、4、5]
v2 = range(1, 6, 2)  # 生成的数为：[1、3、4]
v3 = range(6, 1, -1)  # 生成的数为：[6、5、4、3、2]

# -------------------------------------
# 3.利用for循环和range打印出下面列表的索引
li = ["alex", "WuSir", "ritian", "barry", "wenzhou"]
for i in range(len(li)):
    print(i, li[i])

# -------------------------------------
# 4.利用for循环和range从100~1，倒序打印
for i in range(100, 0, -1):
    print(i)

# -------------------------------------
# 5.利用for循环和range循环1-30的数字
# 将能被3整除的添加到一个列表中，将能被4整除的添加到另外一个列表中
l1 = []
l2 = []
for i in range(31):
    if i % 3 == 0 and i != 0:
        l1.append(i)
    if i % 4 == 0 and i != 0:
        l2.append(i)
print(l1, l2)

# -------------------------------------
# 6.判断 (1,) == 1,
(1,) == 1,  # (False,)   因为被解析为((1,) == 1),

```























<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/pythonav-day02/" target="_blank">https://zhengyang.wang/pythonav-day02</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>