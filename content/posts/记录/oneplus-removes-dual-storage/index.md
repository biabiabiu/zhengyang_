---
title: "OnePlus去除应用双开存储空间"
date: 2021-12-17T18:30:45+08:00
draft: false
tags: ["手机","记录"]
categories: ["生活"]
---





记录了我的一加手机在关闭双开应用功能后如何抹除应用双开存储空间。

<!--more-->

应用双开是在手机文件系统内单独切出一块空间来安置双开的应用，这样就有了主存储空间和应用双开存储空间

一般手机在停止使用应用双开后，这块独立出来的空间会随着被删除，但我的一加5T并没有

<center>
    <img class="jf-image-shadow" src="/images/still-image/oneplus.jpg" title="看着很不爽" height="400px"/>
</center>


双开微信，只是临时用一下，用完卸载后这个所谓的应用双开存储空间却没有被删除，而且系统上也没有提供删除的功能，只能自己想办法给清理掉

经过基友的指点，于是就有了下面的操作

刚好手边有两部手机，利用其中一部**adb connect**到我的一加手机，完成删除。命令大概如下：

```
//列出设备
adb devices
//连接设备
adb connect 192.168.0.129:5555
//获取user列表
adb shell pm list users
//删除 user 999
adb shell pm remove-user 999
```

重启，问题解决！

我的是已经清理过的，所以这里看不到

```
D:\env\adb>adb shell pm list users
Users:        
		UserInfo{0:机主:13} running        
		UserInfo{10:新用户:10}        
		UserInfo{11:访客:14}
```

以上



