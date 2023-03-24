# 笔记本禁用自带键盘


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









