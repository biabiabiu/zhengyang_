---
title: "Linux下配置Clash"
description:  "Linux下配置clash"
keywords: ["clash","代理"]

date: 2022-03-19T16:01:14+08:00
draft: false

tags: ["Linxu","Clash"]
categories: ["Linux"]
---

记录了我在Linux环境配置Clash的过程。

<!--more-->

在windows上使用梯子很方便，SSR、V2等都是图形化界面，很容易操作。最近换到了Linux环境，代理需要配置一下

也是第一次配置，记录如下

## 安装
首先需要在[clash](https://github.com/Dreamacro/clash/releases)下载对应版本的二进制包，我这里下载的是[clash-linux-amd64-v1.9.0](https://github.com/Dreamacro/clash/releases/download/v1.9.0/clash-linux-amd64-v1.9.0.gz)

#### 解压

```bash
gzip -d clash-linux-amd64-v1.9.0.gz 
```
#### 赋予执行权限

```bash
chmod +x clash-linux-amd64-v1.9.0
```
&nbsp;

单独放置

```bash
mkdir l_clash && mv clash-linux-amd64-v1.9.0 l_clash
```

#### 下载配置文件

```bash
cd l_clash
wget -O config.yaml [订阅链接https://...]
```
&nbsp;

首次运行，自动生成`Country.mmdb`

```bash
# -d表示指定当前文件夹为configuration directory
zhengyang@zhengyangpc:~/Downloads/l_clash$ ./clash-linux-amd64-v1.9.0 -d .
INFO[0000] Can't find MMDB, start download              
INFO[0002] Start initial compatible provider Proxy      
INFO[0002] Start initial compatible provider Domestic   
INFO[0002] Start initial compatible provider GlobalTV   
INFO[0002] Start initial compatible provider AsianTV    
INFO[0002] Start initial compatible provider Others     
INFO[0002] RESTful API listening at: [::]:9090
```
#### 设置系统代理



<center>
    <img class="jf-image-shadow" src="/images/still-image/linux-config-clash-1231.png" title="图1" height="100%" />
</center>


#### 验证是否成功

```bash
zhengyang@zhengyangpc:~$ curl https://twitter.com/
<!DOCTYPE html>
<html dir="ltr" lang="en">
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=0,viewport-fit=cover" />
...
```
&nbsp;

或浏览器中访问`www.google.com`

&nbsp;

<center>
    <img class="jf-image-shadow" src="/images/still-image/linux-config-clash-1233.png" title="图None" height="100%" />
</center>

## 配置

#### 修改配置文件



```bash
sudo nano config.yaml
```
大部分是不需要修改的

```yaml
# HTTP 代理端口
port: 7890

# SOCKS5 代理端口
socks-port: 7891

# Linux 和 macOS 的 redir 代理端口
redir-port: 7892

# 允许局域网的连接
allow-lan: true

# 规则模式：Rule（规则） / Global（全局代理）/ Direct（全局直连）
mode: rule

# 设置日志输出级别 (默认级别：silent，即不输出任何内容，以避免因日志内容过大而导致程序内存溢出）。
# 5 个级别：silent / info / warning / error / debug。级别越高日志输出量越大，越倾向于调试，若需要请自行开启。
log-level: silent
# Clash 的 RESTful API
external-controller: '0.0.0.0:9090'

# RESTful API 的口令
secret: '12345678' # 密码可以设置简单些，也可以不用设置

# 您可以将静态网页资源（如 clash-dashboard）放置在一个目录中，clash 将会服务于 `RESTful API/ui`
# 参数应填写配置目录的相对路径或绝对路径。
# external-ui: folder
```
#### WebUI

可以在 [http://clash.razord.top](http://clash.razord.top/) 中进行切换节点等设置

<center>
    <img class="jf-image-shadow" src="/images/still-image/linux-config-clash-1232.png" title="图2" height="100%" />
</center>



也可以使用本地`external-ui`，直接使用Clash提供的Web服务
```bash
git clone https://github.com/Dreamacro/clash-dashboard.git
cd clash-dashboard
git checkout -b gh-pages origin/gh-pages  # 记得切换
```
&nbsp;

在`config.yaml`中引入外部控制UI的路径

```yaml
# 您可以将静态网页资源（如 clash-dashboard）放置在一个目录中，clash 将会服务于 `RESTful API/ui`
# 参数应填写配置目录的相对路径或绝对路径。
external-ui: ./clash-dashboard
```
启动clash后访问 [0.0.0.0:9090/ui](http://0.0.0.0:9090/ui)，一样的效果。此时并没有通过代理来访问

&nbsp;

设置好代理，可以正常使用



<center>
    <img class="jf-image-shadow" src="/images/still-image/linux-config-clash-1233.png" title="图3" height="100%" />
</center>

结束使用时再将系统代理关闭即可


