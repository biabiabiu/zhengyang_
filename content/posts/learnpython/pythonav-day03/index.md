---
title: "Python学习-Day03"
description:  "这里记录了我学习python的过程"
keywords: ["python","自学"]

date: 2022-03-01T17:35:55+08:00
draft: false

tags: ["Python"]
categories: ["Python"]
---

Python学习的第三篇日志。

<!--more-->

#### Python学习-Day03

今天学习了第七章数据类型(三)种的内容，`字典dict`和`集合set`

```python
# 相比较于元组和列表，字典的元素必须是 键值对
# 在Python3.6+ dict为有序的
# dict的键 必须可哈希  可哈希(hashable,不可改变，其生命周期内保持不变)的类型：int/bool/str/tuple；不可哈希的类型：list/dict/set
# 集合有三特殊特点：子元素不重复、子元素必须可哈希、无序
# -------------------------------------
# 练习题
# -------------------------------------
# 1.根据需求写代码
dic1 = {'k1': "v1", "k2": "v2", "k3": [11, 22, 33]}
# 请在字典中添加一个键值对，"k4": "v4"，输出添加后的字典
dic1['k4'] = 'v4'
print(dic1)
# 请在修改字典中 "k1" 对应的值为 "alex"，输出修改后的字典
dic1['k1'] = 'alex'
print(dic1)
# 请在k3对应的值中追加一个元素 44，输出修改后的字典
dic1['k3'].append(44)
print(dic1)
# 请在k3对应的值的第 1 个位置插入个元素 18，输出修改后的字典
dic1['k3'].insert(0, 18)
print(dic1)

# -------------------------------------
# 2.根据需求写代码
dic2 = {
    'name': ['alex', 2, 3, 5],
    'job': 'teacher',
    'oldboy': {'alex': ['python1', 'python2', 100]}
}
# 将name对应的列表追加⼀个元素’wusir’
dic2['name'].append('wusir')
print(dic2)
# 将name对应的列表中的alex⾸字⺟⼤写
dic2['name'][0] = dic2['name'][0].capitalize()
print(dic2)
# oldboy对应的字典加⼀个键值对’⽼男孩’,’linux’
dic2['oldboy']['老男孩'] = 'linux'
print(dic2)
# 将oldboy对应的字典中的alex对应的列表中的python2删除
del dic2['oldboy']['alex'][1]
print(dic2)

# -------------------------------------
# 3.循环提示用户输入，并将输入内容添加到字典中 如果输入N或n则停止循环
dic3 = {}
while True:
    userInput = input("请输入 name|age : ")
    if 'n' in userInput or 'N' in userInput:
        break
    dic3[userInput.split('|')[0]] = userInput.split('|')[1]
print(dic3)

# -------------------------------------
# 4.写代码实现
v1 = {'alex', '武sir', '肖大'}
v2 = []
# 循环提示用户输入，如果输入值在v1中存在，则追加到v2中，如果v1中不存在，则添加到v1中。
# 如果输入N或n则停止循环
while True:
    userInput = input("请输入：")
    if 'n' in userInput or 'N' in userInput:
        print("退出")
        break
    if userInput in v1:
        v2.append(userInput)
    else:
        v1.add(userInput)
print(v1, v2)

# -------------------------------------
# 5.判断以下值那个能做字典的key ？那个能做集合的元素？
li1 = [
    1,  # int hashable,既可以dict也可set
    -1,  # 同上
    '',  # str hashable,dict和set
    None,  # None同样是 immutable object,hashable,dict和set
    [1, 2],  # list为mutable object,unhashable,不可以
    (1,),  # tuple为immutable object,hashable,可以
    {11, 22, 33, 4},  # set为mutable object,unhashable,不可以
    {'name': 'wupeiq', 'age': 18}  # dict为mutable object,unhashable,不可以
]

# -------------------------------------
# 6.将字典的键和值分别追加到 key_list 和 value_list 两个列表中
keyList = []
valueList = []
dict1 = {'k1': 'v1', 'k2': 'v2', 'k3': 'v3'}
for key, value in dict1.items():
    keyList.append(key)
    valueList.append(value)
print(keyList, valueList)

# -------------------------------------
# 7.字典dic = {‘k1’: “v1”, “k2”: “v2”, “k3”: [11,22,33]}
dic7 = {'k1': 'v1', 'k2': 'v2', 'k3': [11, 22, 33]}
# a. 请循环输出所有的key
for key in dic7.keys():
    print(key)
# b. 请循环输出所有的value
for value in dic7.values():
    print(value)
# c. 请循环输出所有的key和value
for key, value in dic7.items():  # 没有items方法默认循环keys
    print(key, value)
# d. 请在字典中添加一个键值对，"k4": "v4"，输出添加后的字典
dic7['k4'] = 'v4'
print(dic7)
# e. 请在修改字典中 "k1" 对应的值为 "alex"，输出修改后的字典
dic7['k1'] = 'alex'
print(dic7)
# f. 请在k3对应的值中追加一个元素 44，输出修改后的字典
dic7['k3'].append(44)
print(dic7)
# g. 请在k3对应的值的第 1 个位置插入个元素 18，输出修改后的字典
dic7['k3'].insert(0, 18)
print(dic7)

# -------------------------------------
# 8.请循环打印k2对应的值中的每个元素
info = {
    'k1': 'v1',
    'k2': ['alex', 'wupeiqi', 'oldboy'],
}
for i in info['k2']:
    print(i)

# -------------------------------------
# 9.有字符串'k: 1|k1:2|k2:3 |k3 :4' 处理成字典 {'k': 1, 'k1': 2…}
dic9 = {}
str9 = 'k:1|k1:2|k2:3|k3:4'
li9 = list(str9.split("|"))
for item in li9:
    k, v = item.split(':')
    dic9[k] = v
print(dic9)

# -------------------------------------
"""
10.有如下值 li= [11,22,33,44,55,66,77,88,99,90]
将所有大于 66 的值保存至字典的第一个key对应的列表中
将小于 66 的值保存至第二个key对应的列表中。
result = {'k1':[],'k2':[]}
"""
li10 = [11, 22, 33, 44, 55, 66, 77, 88, 99, 90]
result = {'k1': [], 'k2': []}
for li in li10:
    if li > 66:
        result['k1'].append(li)
    elif li == 66:
        pass
    else:
        result['k2'].append(li)
print(result)

# -------------------------------------
"""
商品列表：
  goods = [
        {"name": "电脑", "price": 1999},
        {"name": "鼠标", "price": 10},
        {"name": "游艇", "price": 20},
        {"name": "美女", "price": 998}
    ]
要求:
1：页面显示 序号 + 商品名称 + 商品价格，如：
      1 电脑 1999 
      2 鼠标 10
      ...
2：用户输入选择的商品序号，然后打印商品名称及商品价格
3：如果用户输入的商品序号有误，则提示输入有误，并重新输入。
4：用户输入Q或者q，退出程序。
"""
goods = [
    {"name": "电脑", "price": 1999},
    {"name": "鼠标", "price": 10},
    {"name": "游艇", "price": 20},
    {"name": "美女", "price": 998}
]
userChoose = ['1', '2', '3', '4', 'q', 'Q']
for i in range(len(goods)):
    print(i+1, goods[i]['name'], goods[i]['price'])
print("输入'Q'或'q'退出")
while True:
    userInput = input("请输入商品的序号：")
    if userInput not in userChoose:
        print("输入有误，请重新输入！")
        continue
    if userInput.upper() == 'Q':
        print("退出")
        break
    print(goods[int(userInput)-1]['name'], goods[int(userInput)-1]['price'])

```




