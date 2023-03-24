# Linux下使用ResilioSync


记录了我在Linux下安装配置`ResilioSync`的过程。

<!--more-->

这边有两台计算机，一个系统为`ubuntu 20.04`，另一部为`windows11`。两台设备之间的文件传输是必不可少的。

跨平台传文件，如果是局域网内，最方便就是通过FTP来互传文件了，手机上安装一个局域网精灵类似的软件，就可以实现。

`Snapdrop.net`我也有试过，传一段文字或图片类的小文件非常方便，可能是我的姿势不对，这个网站经常失效。

有用过`Resilio Sync`这款软件，虽然没感觉有多么好用，不过还是给装上了。

这里便记录一下安装配置的过程。

## 下载

进入[Resilio Sync下载页面](https://www.resilio.com/individuals/)，选择合适的包

- [i386](https://download-cdn.resilio.com/stable/linux-i386/resilio-sync_i386.tar.gz)
- [x64](https://download-cdn.resilio.com/stable/linux-x64/resilio-sync_x64.tar.gz) 
- [i386 (glibc 2.3)](https://download-cdn.resilio.com/stable/linux-glibc-i386/resilio-sync_glibc23_i386.tar.gz)
- [x64 (glibc 2.3)](https://download-cdn.resilio.com/stable/linux-glibc-x64/resilio-sync_glibc23_x64.tar.gz) 
- [ARM](https://download-cdn.resilio.com/stable/linux-arm/resilio-sync_arm.tar.gz)
- [ARMHF](https://download-cdn.resilio.com/stable/linux-armhf/resilio-sync_armhf.tar.gz)

## 安装

解压

```bash
tar -zxvf resilio-sync_x64.tar.gz
# LICENSE.TXT
# rslsync
```

开启服务

```bash
./rslsync
```

```
By using this application, you agree to our Privacy Policy, Terms of Use and End User License Agreement.
https://www.resilio.com/legal/privacy
https://www.resilio.com/legal/terms-of-use
https://www.resilio.com/legal/eula

Resilio Sync forked to background. pid = 4693
```

## 配置

ResilioSync在Linux平台并没有图形界面，只能在Web页面使用

浏览器打开`http://localhost:8888/gui/`进入WebUI，设置好`username`和`passwd`便可以进入。后续进入都需要输入密码。

<center>
    <img class="jf-image-shadow" src="/images/still-image/Sync-on-Linux-login.png" title="Login" height="100%" />
</center>



可以在`General`配置页面语言以及`WebUI`的端口等等

> ResilioSync的[Guide To Linux, And Sync Peculiarities](https://help.resilio.com/hc/en-us/articles/204762449-Guide-to-Linux-and-Sync-peculiarities)



