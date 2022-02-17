---
title: "DIR批量获取文件名"
description:  "快速的将当前目录下所有文件的文件名整理到一表格内"
keywords: ["DIR","文件名"]

date: 2020-08-31T23:07:05+08:00
draft: false

tags: ["Windows","DIR命令"]
categories: ["Windows"]
---



快速的将当前目录下所有文件的文件名整理到一表格内。

<!--more-->

Windows的`DIR`命令类似于Linux的`ls`，用来查看目录下文件

`DIR`不带参数默认返回的内容包括该文件的`Mode、LastWriteTime、Length和Name`属性，这里我只需要获取它的`Name`即可

```powershell
DIR *.* /B > fileName.csv // 翻译：在当前目录下遍历所有文件并将文件名(含后缀)重定向至`fileName.csv`文件
// DIR是命令
// "*.*" 当前文件夹下所有的文件
// "/B" 我只想获取文件名
// "> fileName.csv" 将返回的内容输出重定向至fileName.csv文件；CSV是通用文件，记事本和Excel都可以打开
```
```powershell
DIR *.* /B /A-D > fileName.csv
//只获取目录下文件的命名，不包含文件夹
```

要用到的命令`DIR`，下面是关于该命令的帮助文档

```powershell
DIR [drive:][path][filename] [/A[[:]attributes]] [/B] [/C] [/D] [/L] [/N]
  [/O[[:]sortorder]] [/P] [/Q] [/R] [/S] [/T[[:]timefield]] [/W] [/X] [/4]
  [drive:][path][filename]
              指定要列出的驱动器、目录和/或文件。
  /A          显示具有指定属性的文件。
  属性         D  目录                R  只读文件
               H  隐藏文件            A  准备存档的文件
               S  系统文件            I  无内容索引文件
               L  重新分析点          O  脱机文件
               -  表示“否”的前缀
  /B          使用空格式(没有标题信息或摘要)。
  /C          在文件大小中显示千位数分隔符。这是默认值。用 /-C 来
              禁用分隔符显示。
  /D          跟宽式相同，但文件是按栏分类列出的。
  /L          用小写。
  /N          新的长列表格式，其中文件名在最右边。
  /O          用分类顺序列出文件。
  排列顺序     N  按名称(字母顺序)     S  按大小(从小到大)
               E  按扩展名(字母顺序)   D  按日期/时间(从先到后)
               G  组目录优先           -  反转顺序的前缀
  /P          在每个信息屏幕后暂停。
  /Q          显示文件所有者。
  /R          显示文件的备用数据流。
  /S          显示指定目录和所有子目录中的文件。
  /T          控制显示或用来分类的时间字符域
  时间段      C  创建时间
              A  上次访问时间
              W  上次写入的时间
  /W          用宽列表格式。
  /X          显示为非 8dot3 文件名产生的短名称。格式是 /N 的格式，
              短名称插在长名称前面。如果没有短名称，在其位置则
              显示空白。
  /4          以四位数字显示年份
```



<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/dir-get-foldername/" target="_blank">https://zhengyang.wang/dir-get-foldername</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>