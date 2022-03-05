---
title: "Python学习-Day05"
description:  "这里记录了我学习python的过程"
keywords: ["python","练习","自学"]

date: 2022-03-06T00:56:35+08:00
draft: false

tags: ["Python"]
categories: ["Python"]
---

python的一些练习题。

<!--more-->

`Pythonav`的内容自`函数`部分及后续就没有设置练习题，于是便去找了其他的练习题集

1. **Python 小例子**[中文]

   [项目地址](https://github.com/jackzhenguo/python-small-examples)

2. **PythonTip**[中文]

   [项目地址](http://www.pythontip.com/)

3. **Python - 100天**[中文]

   [项目地址](https://github.com/jackfrued/Python-100-Days)

4. **PythonChallenge**[英文]

   [项目地址](http://www.pythonchallenge.com/)



#### 今日练习部分

{{< admonition question "练习一" false>}}
一个字符串 a， 输出逆序之后的a。
例如：a='xydz'，则输出：zdyx
{{< /admonition >}}

1. 利用切片步长进行排序

   ```python
   print(''.join(list(a)[::-1]))
   ```

2. 利用`list.reverse`进行排序

   ```python
   a = 'xydz'
   b = [str(i) for i in list(a)]
   b.reverse()
   print(''.join(b))
   ```

   

{{< admonition question "练习二" false>}}
a={1:1,2:2,3:3}，输出a的key，以','连接。要求key以**字典序升序**排列，key可以是字符串
如：a={1:1,2:2,3:3}, 则输出：1,2,3
{{< /admonition >}}

```python
','.join(str(i) for i in sorted([int(i) for i in a.keys()]))
```



{{< admonition question "练习三" false>}}
输出字符串a中奇数位置字符构成的字符串(位置编号从1开始)。
例如：a='xyzwd'，则输出:xzd
{{< /admonition >}}

```python
list1 = []
for i in a:
    if (a.find(i) + 1) % 2 != 0:
        list1.append(i)
print(''.join(list1))
```



{{< admonition question "练习四" false>}}
[在屏幕上显示跑马灯文字](https://github.com/jackfrued/Python-100-Days/blob/master/Day01-15/07.%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%92%8C%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84.md#%E7%BB%83%E4%B9%A01%E5%9C%A8%E5%B1%8F%E5%B9%95%E4%B8%8A%E6%98%BE%E7%A4%BA%E8%B7%91%E9%A9%AC%E7%81%AF%E6%96%87%E5%AD%97)
{{< /admonition >}}

```python
import os
import time

content = '全场都2元...'
while True:
    os.system('cls')
    print(content)
    time.sleep(0.2)
    content = content[1:] + content[0]
```







<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/python-day05/" target="_blank">https://zhengyang.wang/python-day05</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>