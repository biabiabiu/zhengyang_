---
title: "笔记本禁用自带键盘"
description:  "笔记本禁用自带键盘"
keywords: ["键盘","笔记本"]

date: 2022-03-06T16:58:30+08:00
draft: false

tags: ["windows键盘"]
categories: ["Windows","记录"]
---

记录了如何禁用笔记本自带键盘的方法。

<!--more-->

我的笔记本电脑用的是另外购置的键盘，自带键盘很少用到。桌子也比较窄，宽度刚好可以放下一电脑，再放上一个键盘总会误触到自带的键

为了解决这个麻烦，想到将其自带键盘禁用，只用外接的键盘，尝试在设备管理器中把自带键盘禁用或卸载驱动，但都无效

有网友给出了解决办法

{{< admonition >}}
需要管理员运行，返回`SUCCESS`的字样表示成功。之后需要重启
{{< /admonition >}}

**打开键盘禁用**

```powershell
sc config i8042prt start= disabled
```

**关闭键盘禁用**

```powershell
sc config i8042prt start= demand
```



> 参考文章
>
> [win10系统禁用笔记本自带键盘的有效方法](https://www.chenxublog.com/2016/08/12/win10-disable-keybroad.html)









<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/disable-keyboard/" target="_blank">https://zhengyang.wang/disable-keyboard</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>