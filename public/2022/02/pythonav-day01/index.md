# Python学习-Day01


Python学习的第一篇日志。

<!--more-->

#### 开篇

虽然我现在的工作完全用不到编程

不过我相信，不论是现在的`信息互联网`，或是未来的`价值互联网`时代，拥有一定的编程开发能力，对我的成长和工作都会有较大的帮助，也顺便拓宽一下自己的技能树

最终选择了`Python`

目前是以`武沛齐`老师的[pythonav](https://pythonav.com)教程为基础，结合`廖雪峰`老师的[python教程](https://www.liaoxuefeng.com/wiki/1016959663602400)和[菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html)来完成Python的基础学习

希望自己能坚持下去，坚持练习，坚持把学习、练习的过程以日志的形式记录，加油！

#### Python学习-Day01

第一天简单过一遍前四章内容，以及第五章的数据类型(一)，将其练习题挨个完成一遍

```python
# 练习题：获取用户输入的字符判断他的数字的字符串中有一个数字（只考虑个位数）
# 例如 '你有点2，还特么有点666' 这段字符串中有4个数字
data = input("请输入：")
index = 0
list1 = []
while len(data) > index:
    if data[index].isdecimal():
        list1.append(data[index])
        index += 1
    else:
        index += 1
print("有%s个数字" % len(list1))

# ----------------------------------
# 作业题
# 有变量
name = "aleX leNb "
# 移除 name 变量对应的值两边的空格,并输出处理结果
print(name.strip())
# 判断 name 变量是否以 “al” 开头,并输出结果（用切片）
print(name.strip()[0:2] == "al")
# 判断name变量是否以”Nb”结尾,并输出结果（用切片）
print(name.strip()[-2:] == "Nb")
# 将 name 变量对应的值中的 所有的”l” 替换为 “p”,并输出结果
print(name.replace("l", "p"))
# 将name变量对应的值中的第一个”l”替换成”p”,并输出结果
# str.replace(old, new[, max])
# old -- 将被替换的子字符串。
# new -- 新字符串，用于替换old子字符串。
# max -- 可选字符串, 替换不超过 max 次
print(name.replace("l", "p", 1))
# 将 name 变量对应的值根据 所有的”l” 分割,并输出结果
print(name.split('l'))
# 将name变量对应的值根据第一个”l”分割,并输出结果
# str.split(str="", num=string.count(str)).
# str -- 分隔符，默认为所有的空字符，包括空格、换行(\n)、制表符(\t)等。
# num -- 分割次数。默认为 -1, 即分隔所有。
print(name.split('l', 1))
# 将 name 变量对应的值变大写,并输出结果
print(name.upper())
# 将 name 变量对应的值变小写,并输出结果
print(name.lower())
# 请输出 name 变量对应的值的第 2 个字符
print(name[1])
# 请输出 name 变量对应的值的前 3 个字符
print(name[0:3])
# 请输出 name 变量对应的值的后 2 个字符
print(name[-3:-1])

# ---------------------------------
# 有字符串
s = '123a4b5c'
# 通过对s切片形成新的字符串 “123”
print(s[0:3])
# 通过对s切片形成新的字符串 “a4b”
print(s[3:6])
# 通过对s切片形成字符串s5,s5 = “c”
print(s[-1])
# 通过对s切片形成字符串s6,s6 = “ba2”
print(s[5:0:-2])

# ----------------------------------
# 使用while和for循环字符串 s=”asdfer” 中每个元素。
while
s2 = "asdfer"
index = 0
while len(s2) > index:
    print(s2[index])
    index += 1
# for
for i in s2:
    print(i)

# ----------------------------------
# 使用while和for循环对s=”321”进行循环
# 打印的内容依次是：”倒计时3秒”，”倒计时2秒”，”倒计时1秒”，”出发！”
# 略
# ----------------------------------
# 使用while和for循环分别对字符串
message = “伤情最是晚凉天，憔悴厮人不堪言。” 进行打印
msg = "伤情最是晚凉天，憔悴厮人不堪言。"
count = 0
while len(msg) > count:
    print(msg[count])
    count = count + 1

# ----------------------------------
# 获取用户输入的内容，并计算前四位”l”出现几次,并输出结果。
user_input = input("请输入：")
count_num = 0
for i in user_input[0:4]:
    if i == 'l':
        count_num += 1
print("前四位中输入了%s次'l'" % count_num)

# ----------------------------------
# 获取用户两次输入的内容，将其中所有的数字获取并进行相加
input1 = input("第一次输入：")
input2 = input("第二次输入：")
num1, num2 = '', ''
for i in input1:
    if i.isdecimal():
        num1 = num1 + i
for i in input2:
    if i.isdecimal():
        num2 = num2 + i
print(num1, num2, int(num1)+int(num2))

```



















