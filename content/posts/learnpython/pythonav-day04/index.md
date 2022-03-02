---
title: "Python学习-Day04"
description:  "这里记录了我学习python的过程"
keywords: ["python","自学"]

date: 2022-03-02T23:45:16+08:00
draft: false

tags: ["Python"]
categories: ["Python"]
---

学习Python的第四篇日志。

<!--more-->

#### Python学习-Day04

今天将第八章的试题练习了一下。`浅拷贝`和`深拷贝`

```python
# -------------------------------------------
# 笔试题(部分)
# -------------------------------------------
# 12.写代码实现将字符串 v = “全栈21期” 反转
v = '我吃西红柿'
li = list(v)
li.reverse()
print(li)

# -------------------------------------------
# 13.看结果写结果
info = [
    {'k1': 1, 'k2': {'k9': 'oldboy', 'k10': '一天天'}},
    (11, 22, 33, 44),
    {199, 2, 3, 4, 5},
    True,
    ['武沛齐', '景女神', {'extra': ("alex", 'eric', [18, 20])}]
]
# 根据索引获取上述结构中的 1
print(info[0]['k1'])
# 请根据索引获取上述结构中的 “oldboy”
print(info[0]['k2']['k9'])
# 请根据索引获取上述结构中的 44
print(info[1][-1])
# 根据索引获取上述结构中的 “天天”
print(info[0]['k2']['k10'][-2:])
# 请循环打印 上述结构 中的集合
for i in info[2]:
    print(i)  # 无序
# 在上述结构中 extra 所在的字典中添加一个键值对，并设置键为：True, 值为 ”真“
info[-1][-1][True] = "真"
print(info)
# 请在上述结构中 [18,20] 中添加一个整型元素：69
info[-1][-1]['extra'][-1].insert(1, 69)
print(info)

# -------------------------------------------
# 14.看代码写结果
# 布尔"与" - 如果 x 为 False，x and y 返回 x 的值，否则返回 y 的计算值。
result = 1 > 6 and 8 < 9  # 优先级：比较运算符>赋值运算符>逻辑运算符 False and True  >> False
print(result)  # False
# 布尔"或" - 如果 x 是 True，它返回 x 的值，否则它返回 y 的计算值
result = 1 or 2
print(result)  # 1
result = 0 or True
print(result)  # True
# and有更高的优先级
result = 1 and 8 or True and 4  # >> 8 or 4 >> 8
print(result)  # 8
result = 'Alex' or '' and 'oldboy'  # >> 'Alex' or False >> 'Alex'
print(result)  # 'Alex'

# -------------------------------------------
# 15.写代码实现实现将字符串 v = “k1|v1,k2|v2,k3|v3…” 转换成字典 {‘k1’:’v1’,’k2’:’v2’,’k3’:’v3’..}
v = 'k1|v1,k2|v2,k3|v3'
vDict = {}
v1 = v.split(",")
print(v1)
for i in v1:
    vDict[i.split("|")[0]] = i.split("|")[1]
print(vDict)

# -------------------------------------------
# 16.实现一个整数乘法计算器,输入：5*9*99.... 或5* 9 * 10 * 99 或5 * 9 * 99（含空白）
x = []
content = input("请输入算式：")
con_list = content.split("*")
for i in con_list:
    i.strip()
    x.append(i)
count = 1
for i in x:
    count *= int(i)
print(count)

# -------------------------------------------
# 17.看代码写v1, v2?
# 传递了地址，修改了地址的值
v1 = [1, 2, 3, 4, 5]
v2 = [v1, v1, v1]
v2[1][0] = 111
v2[2][0] = 222
print(v1)  # [222, 2, 3, 4, 5]
print(v2)  # [[222, 2, 3, 4, 5], [222, 2, 3, 4, 5], [222, 2, 3, 4, 5]]

# -------------------------------------------
# 18.请将info中索引值为偶数的值使用 “*” 拼接起来，并写入到文件 b.txt 中
info = ['你是', '到底', '是', '不是', '一个', '魔鬼']
list1 = []
for i in range(len(info)):
    if i % 2 == 0:
        list1.append(info[i])
str1 = "*".join(list1)
print(str1)
f = open('b.txt', mode='w', encoding='utf-8')
f.write(str1)
f.flush()
f.close()

# -------------------------------------------
# 机试题
# -------------------------------------------
# 1.根据车牌信息，分析出各省的车牌持有数量
cars = ['鲁A32444', '鲁B12333', '京B8989M', '黑C49678', '黑C46555', '沪B25041', '黑C34567', '沪A46556']
info = {'鲁': 0, '黑': 0, '京': 0, '沪': 0}
for car in cars:
    if car[0] == '鲁':
        info['鲁'] += 1
    elif car[0] == '京':
        info['京'] += 1
    elif car[0] == '黑':
        info['黑'] += 1
    else:
        info['沪'] += 1
print(info)

# -------------------------------------------
# 2.利用文件操作，将其构造成如下数据类型。
# # data.txt文件内容如下
#     id,name,age,phone,job
#     1,alex,22,13651054608,IT
#     2,wusir,23,13304320533,Tearcher
#     3,taibai,18,1333235322,IT
# info = [{'id':'1','name':'alex','age':'22','phone':'13651054608','job':'IT'},......]
dic = []
dic2 = []
info = {}
f = open('b.txt', mode='r', encoding='utf-8')
import copy
for line in f:
    dic.append(line.strip().split(','))
titleList = dic.pop(0)
print(dic)
for i in dic:
    for j in range(len(i)):
        info[titleList[j]] = i[j]
    dic2.append(copy.deepcopy(info))
print(dic2)

# -------------------------------------------
# 3.请使用for循环打印 9*9乘法表
for i in range(10):
    for j in range(i):
        print(" %s*%s=%s " % (i, j+1, i*(j+1)), end='')
    print('')

```



<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/pythonav-day04/" target="_blank">https://zhengyang.wang/pythonav-day04</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>