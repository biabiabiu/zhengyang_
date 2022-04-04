---
title: "Linux设置自动禁用键盘"
description:  "记录了Linux自动禁用笔记本键盘的过程"
keywords: ["linux","禁用键盘","笔记本"]

date: 2022-04-04T18:02:36+08:00
draft: false

tags: ["键盘禁用"]
categories: ["Linux","记录"]
---

这篇记录了我为Linux设置自动禁用笔记本键盘的过程。

<!--more-->

## 前言

最近切换到Liunx，感觉非常不错。使用了GNOME、GNOME Shell 扩展来定制桌面

<center>
    <img class="jf-image-shadow" src="/images/still-image/linux-capture-220404.png" title="LinuxDesktop" height="100%" width="80%"/>
</center>

遇到了同样的问题—**键盘禁用**，前面有提到[windows平台如何禁用笔记本键盘](https://zhengyang.wang/disable-keyboard/)，CMD敲下命令，只要不进行系统更新，键盘可一直保持禁用状态

可Linux不这样，禁用只对本次启动有效，后续重启后都需要再次执行命令，非常麻烦。最好是能有一个禁用脚本，在进入系统时自动执行

## 键盘禁用

Linux平台，可以用`xinput`来禁用/启用输入设备

```shell
xinput disable <device> # 禁用设备
xinput enable <device> # 启动设备
```

这里以Ubuntu为例，当前环境

```shell
zhengyang@zhengyangpc:~$ uname -a
Linux zhengyangpc 5.13.0-39-generic #44~20.04.1-Ubuntu SMP Thu Mar 24 16:43:35 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

#### 手动禁用

###### 获取输入设备

```shell
zhengyang@zhengyangpc:~$ xinput list
⎡ Virtual core pointer                        id=2    [master pointer  (3)]
⎜   ↳ Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
⎜   ↳ MOSART Semi. Mi Wireless Combo Mouse        id=12    [slave  pointer  (2)]
⎜   ↳ MOSART Semi. Mi Wireless Combo Consumer Control    id=13    [slave  pointer  (2)]
⎜   ↳ 2.4G Mouse                                  id=15    [slave  pointer  (2)]
⎜   ↳ FocalTechPS/2 FocalTech Touchpad            id=19    [slave  pointer  (2)]
⎣ Virtual core keyboard                       id=3    [master keyboard (2)]
    ↳ Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    ↳ Power Button                                id=6    [slave  keyboard (3)]
    ↳ Asus Wireless Radio Control                 id=7    [slave  keyboard (3)]
    ↳ Video Bus                                   id=8    [slave  keyboard (3)]
    ↳ Video Bus                                   id=9    [slave  keyboard (3)]
    ↳ Sleep Button                                id=10    [slave  keyboard (3)]
    ↳ MOSART Semi. Mi Wireless Combo              id=11    [slave  keyboard (3)]
    ↳ MOSART Semi. Mi Wireless Combo System Control    id=14    [slave  keyboard (3)]
    ↳ USB2.0 VGA UVC WebCam: USB2.0 V             id=16    [slave  keyboard (3)]
    ↳ Asus WMI hotkeys                            id=17    [slave  keyboard (3)]
    ↳ MOSART Semi. Mi Wireless Combo Consumer Control    id=20    [slave  keyboard (3)]
    ↳ AT Translated Set 2 keyboard                id=18    [slave  keyboard (3)]
```

在输出中找到需要禁用设备的`id`，一般笔记本自带键盘为`AT Translated Set 2 keyboard`。此时的`id`值为18

{{< admonition >}}

这里的id值并不是固定的

{{< /admonition >}}

###### 禁用

```shell
zhengyang@zhengyangpc:~$ xinput disable 18
```

默认是没有输出的，此时自带的键盘便失去作用了

###### 使用正则匹配

每次禁用都需要敲两条命令，我希望一条就可以解决

```shell
xinput disable `xinput list | grep AT | egrep -o "id=[0-9]*" | egrep -o "[0-9]*"`
```

1. 在list中找到有AT的一行
   
   ```shell
   zhengyang@zhengyangpc:~$ xinput list | grep AT 
    ↳ AT Translated Set 2 keyboard                id=18    [slave  keyboard (3)]
   ```
2. 在该行进行正则匹配，`egrep`默认返回匹配行结果，`-o, --only-matching`只显示行中非空匹配部分，即只返回匹配内容
   
   ```shell
   zhengyang@zhengyangpc:~$ xinput list | grep AT | egrep -o "id=[0-9]*"
   id=18
   ```
3. 再以同样的方式取得id值，最后执行`xinput disable id`

###### 不足之处

这种方式可以直接禁用，且只对本次开机有效，关机重启后需要再次手动执行

#### 自动禁用

每次开机都要重复执行一次比较麻烦，可以直接在每次进入系统时自动禁用

###### crontab

一开始打算使用crontab计划任务，在开机时执行脚本文件自动禁用的

```shell
zhengyang@zhengyangpc:~/Other$ cat dis_keyboard.sh 
# !/bin/bash
# Disable notebook built-in keyboard.
keyboard_id=`xinput list | grep AT | egrep -o "id=[0-9]*" | egrep -o "[0-9]*"`
xinput disable $keyboard_id
```

在crontab中添加开机执行任务

```shell
zhengyang@zhengyangpc:~/Other$ crontab -e
...
# Set up to automatically disable the keyboard
@reboot root /home/zhengyang/Other/dis_keyboard.sh >/dev/null 2>&1
```

但是一直没有效果，到最后也没有发现具体的原因

```shell
zhengyang@zhengyangpc:~/Other$ tail -f /var/log/cron.log
Apr  4 00:54:00 zhengyangpc anacron[919]: Anacron 2.3 started on 2022-04-04
Apr  4 00:54:00 zhengyangpc anacron[919]: Normal exit (0 jobs run)
Apr  4 00:54:00 zhengyangpc cron[923]: (CRON) INFO (pidfile fd = 3)
Apr  4 00:54:00 zhengyangpc cron[923]: (CRON) INFO (Running @reboot jobs)
Apr  4 00:54:00 zhengyangpc CRON[1002]: (zhengyang) CMD (/home/zhengyang/Other/dis_keyboard.sh >/dev/null 2>&1)
```

最终还是选择了修改`.bash_profile`

###### ~/.bash_profile

`.bash_profile`是Linux每个用户自己的专用Shell配置文件，系统会在用户登录时自动执行一次该文件。那么我只需要在其中加入禁用命令即可

{{< admonition >}}
Ubuntu以`~/.profile`代替，同样的作用，目的是为了兼容其他的`Shell`
{{</ admonition >}}

###### 修改~/.profile

使用vim进行编辑

```shell
zhengyang@zhengyangpc:~$ vim .profile
zhengyang@zhengyangpc:~$ cat .profile
...
# Set up to automatically disable the keyboard
xinput disable `xinput list | grep AT | egrep -o "id=[0-9]*" | egrep -o "[0-9]*"`
```

#### 验证

`.bash_profile/.profile`只对当前用户生效。但类似于`/etc/profile`，也需要重启后才会生效

```shell
zhengyang@zhengyangpc:~/Other$ reboot
```



<div style="margin-top:2em;padding:0 0.5em;font-size:.875rem">
    <hr>
    <div style="padding-bottom:1em;">
        <p>本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></p>
        <p>本文链接：<a href="https://zhengyang.wang/linux-autodisable-keyboard/" target="_blank">https://zhengyang.wang/linux-autodisable-keyboard</a></p>
        <p>版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</p>
    </div>
</div>