---
title: "笔记本配置升级—内存、硬盘"
description:  "记录了我为旧笔记本加装内存和硬盘的经历"
keywords: ["双系统","硬件升级","加内存","加硬盘","linux"]

date: 2022-03-30T15:54:49+08:00
draft: false

tags: ["Windows","Linux"]
categories: ["Computer"]
---

记录了旧笔记本升级硬件配置的过程。

<!--more-->

## 前言
女朋友的笔记本是大学时期购买的——`华硕飞行堡垒X550JX`，15年上市，预装Windows10系统。放到现在，硬件已经跟不上软件的迭代，用起来非常卡，打开浏览器大概需要10s。吃灰又有些可惜了

考虑将部分硬件做一下升级，鉴于自身的能力与条件，最终选择加装固态和内存

这是原始硬件配置
```
Windows10
i5-4200H @ 2.80GHz 双核
华硕 X550JX
4GB ( GLOWAY DDR3L 1600MHz )
Toshiba 1T 机械硬盘
Nvidia GeForce GTX 950M ( 2 GB )
友达 AUO36ED ( 15.5 英寸  )
Atheros AR9565 Wireless Network Adapter / Azurewave
```
升级后的配置
```shell
System:
  Kernel: 5.13.0-37-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.4 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: ASUSTeK product: X550JX v: 1.0 serial: <filter> 
  Mobo: ASUSTeK model: X550JX v: 1.0 serial: <filter> 
  BIOS: American Megatrends v: X550JX.209 date: 10/31/2015 
Battery:
  ID-1: BAT0 charge: 28.7 Wh condition: 28.9/41.4 Wh (70%) 
  model: ASUSTeK ASUS Battery status: Not charging 
CPU:
  Topology: Dual Core model: Intel Core i5-4200H bits: 64 type: MT MCP 
  arch: Haswell rev: 3 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 22347 
  Speed: 901 MHz min/max: 800/3400 MHz Core speeds (MHz): 1: 1161 2: 1127 
  3: 1340 4: 1112 
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics vendor: ASUSTeK 
  driver: i915 v: kernel bus ID: 00:02.0 
  Device-2: NVIDIA GM107M [GeForce GTX 950M] vendor: ASUSTeK driver: nvidia 
  v: 450.172.01 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.13 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4600 (HSW GT2) 
  v: 4.5 Mesa 21.2.6 direct render: Yes 
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio 
  driver: snd_hda_intel v: kernel bus ID: 00:03.0 
  Device-2: Intel 8 Series/C220 Series High Definition Audio vendor: ASUSTeK 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.13.0-37-generic 
Network:
  Device-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter 
  vendor: AzureWave driver: ath9k v: kernel port: e000 bus ID: 03:00.0 
  IF: wlp3s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: ASUSTeK driver: r8169 v: kernel port: d000 bus ID: 04:00.1 
  IF: enp4s0f1 state: down mac: <filter> 
Drives:
  Local Storage: total: 1.14 TiB used: 26.93 GiB (2.3%) 
  ID-1: /dev/sda vendor: Toshiba model: MQ01ABD100 size: 931.51 GiB 
  ID-2: /dev/sdb vendor: Teclast model: 256GB SSD size: 238.47 GiB 
Partition:
  ID-1: / size: 46.97 GiB used: 26.90 GiB (57.3%) fs: ext4 dev: /dev/sdb5 
Sensors:
  System Temperatures: cpu: 50.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 2600 
Info:
  Processes: 305 Uptime: 1h 55m Memory: 11.58 GiB used: 4.34 GiB (37.5%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 
```

使用了一段时间，目前没有遇到什么问题

## 配件购买

没有追求极致性价比，图省事直接在京东购买

经查询了解到

- 华硕X550JX是板载内存4GB DDR3 1600 MHz，只预留了一个SODIMM插槽最大支持8GB
- 没有多余硬盘位接口，且只支持SATA，但光驱是假光驱，可以拆卸后加装硬盘光驱位

那么我可以
- 加装一条8GB DDR3L 1600 MHz的内存扩容至12GB
- 将原有的机械硬盘位更换为固态做系统盘
- 拆掉假光驱，加装硬盘托盘放置机械硬盘

于是便购买了
- 台电 256GB SSD ( 256 GB / 固态硬盘 ）|  ￥169.9

- 8GB ( GLOWAY DDR3L 1600MHz / 低电压版 内存条)   |   ￥178.0

- 9mm光驱位硬盘托架   |   ￥9.8

- 多功能螺丝刀套装    |   ￥17.8

  花费合计`375.5`元

## 更换升级
> 其实一开始直接购买了两条内存，拆开后才发现原始的4GB是板载内存，只能加装一个，无奈只好退货。所以下次再搞，要事先清楚这些注意事项。另外写下本文时已经升级完成，就不再特意拆开拍照了

准备好工具，拆卸起来还是比较顺利的，步骤大致如下

- 卸去电池

- 卸去螺丝

- 卸去后盖

  能够看到预留内存插槽，如果只需要加装内存，到这一步就可以了，后续不需要再拆卸

- 卸去键盘(注意键盘主板间连接排线)

- 卸去光驱
  - 托盘固定好硬盘
  - 装入托盘并固定
  
- 顺便清理一下灰尘

- 组装

**拆卸下的光驱**

<center>
    <img class="jf-image-shadow" src="/images/still-image/m-hard-drive.jpg" title="mechanical hard drive" width="80%" />
</center>


## 系统重装
本子出厂预装的是Windows 10，用起来实在是太卡，决定将其后退至Windows 7，重装过程比较顺利，没有遇到报错。以下是安装过程
1. 下载[Windows 7](https://msdn.itellyou.cn/)镜像文件
2. 制作WinPE，这里使用的是[微PE](https://www.wepe.com.cn/)
3. 进入 BIOS 选择 U盘启动，进入WinPE
4. 使用DiskGenius进行分区
5. Windows 7 安装
6. 重启进入系统
   这里出现了一个小插曲，进去系统后无线鼠标和网卡都无法使用，因为没有安装驱动。在官网、驱动精灵、驱动总裁等下载好网卡驱动放入U盘后，插上电脑居然也无法使用，只好在WinPE中将驱动复制到硬盘之后再重启安装，之后才恢复上网

重装后的Windows 7 总是动不动就蓝屏，尝试360修复也不管用，经过漏洞修复，系统更新一番操作，恢复正常了，玄学

## Win7 + Linux
其实笔记本女朋友平时也不怎么用，我又可以继续瞎折腾了，于是便划出50G的空间用来装Ubuntu

<center>
    <img class="jf-image-shadow" src="/images/still-image/ubuntu-desktop.png" title="ubuntu-desktop" width="85%" />
</center>

<center>
    <img class="jf-image-shadow" src="/images/still-image/ubuntu-setting.png" title="ubuntu-setting" width="85%" />
</center>


**下面是Ubuntu的安装过程**

1. 下载Ubuntu.iso镜像文件，国内推荐[清华大学开源软件镜像站](https://mirror.tuna.tsinghua.edu.cn/)，速度更快，更稳定
2. 使用`UltraISO`软碟通刻录启动盘
   这里我使用的是另一款软件—— [Ventoy](https://www.ventoy.net/cn/index.html)，功能同样强大
3. 划分空间，这里我把整个D盘配给Ubuntu
4. 进入 BIOS 选择 U盘启动进行安装，我选择的是断网安装，安装好后再进行update、upgrade等操作，这样可以节省安装时间。另外，我希望Ubuntu可以和Windows 7共存，所以在安装类型选择了两者共存
5. 不出意外的话大概需要5-10分钟就安装完成了
6. 重启，记得拔U盘

重启进入系统时，`GUN GRUB`引导默认是Ubuntu
```shell
*Ubunut
 Ubuntu高级选项
 Memory test (memtest86+)
 Memory test (memtest86+,.....)
 Windows 7 (loader) (on /dev/...)
```
由于这个本子的主人依旧是我女朋友，所以需要将默认启动顺序进行调整。终端输入
```shell
sudo gedit /etc/default/grub
```
**将**

```shell
GRUB_DEFAULT=0  # GRUB默认启动项
GRUB_TIMEOUT=10  # GRUB默认倒计时
```
**修改为**

```shell
GRUB_DEFAULT=4  # 修改为4，即默认启动项为Windows 7
GRUB_TIMEOUT=5  # 修改为5，即默认倒计时为5s
```
**更新配置**

```shell
sudo update-grub
```

## 未来打算
大学期间使用过一段时间Ubuntu，感受是相对简陋的配置下，Linux运行更加流畅。现在Linux也有很多Windows平台的移植软件包，在[优麒麟应用商店](https://www.ubuntukylin.com/applications/)、[deepin-wine](https://github.com/zq1997/deepin-wine)等都能找到，安装非常便捷，只是软件稳定性、流畅性等方面与Windows平台相比还有些欠缺

**在Ubuntu上使用微信**

```shell
wget -O- https://deepin-wine.i-m.dev/setup.sh | sh # 添加仓库
sudo apt-get install com.qq.weixin.deepin
```
这里是已经安装了的
```shell
zhengyang@zhengyangpc:~$ apt list --installed | grep weixin

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

com.qq.weixin.deepin/未知,now 3.4.0.38deepin6 i386 [已安装]
```
**微信使用体验**

<center>
    <img class="jf-image-shadow" src="/images/still-image/ubuntu-weixin-login.png" title="wechat-login"  />
</center>

&nbsp;



<center>
    <img class="jf-image-shadow" src="/images/still-image/ubuntu-weixin-about.png" title="wechat-about" width="85%" />
</center>


**浏览器(Firefox)使用体验**

<center>
    <img class="jf-image-shadow" src="/images/still-image/ubuntu-firefox.png" title="wechat-about" width="85%" />
</center>


**WPS使用体验**

<center>
    <img class="jf-image-shadow" src="/images/still-image/ubuntu-usewps.png" title="Ubuntu-WPS" width="85%" />
</center>


日常使用微信和Excel比较多，在Linux上也有替代，于是就有了从Windows转Linux的想法

打算后续再组装一个台式机，硬盘配置就512G固态+1T机械，分别装Windows和Linux，机械硬盘两者都可以挂载读取。两者又可作为主力使用，Windows上打打游戏，Linux学学开发(有人说使用Liunx本就是学习)

笔记本就不折腾了，Windows养老
