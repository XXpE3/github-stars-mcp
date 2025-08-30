---
project: vps_setup
stars: 854
description: |-
    linux  vim bash 脚本学习笔记 by 蘭雅sRGB   https://262235.xyz/
url: https://github.com/hongwenjun/vps_setup
---

[![GitHub stars](https://img.shields.io/github/stars/hongwenjun/vps_setup)](https://github.com/hongwenjun/vps_setup/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/hongwenjun/vps_setup)](https://github.com/hongwenjun/vps_setup/network)
- :smile: [简体中文](https://github.com/hongwenjun/vps_setup/blob/master/README.md) 　:cry: [English](https://git.io/vps.english)    　 　 　 　 　 　 　 　 　龙芯2F服务器 https://262235.xyz/

## :bell: 我們雖然窮，但是不能說謊，也不能打人；不是我們的東西，我們不能拿；
## :100: 要好好讀書，長大要做個對社會有用的人。

- [![](https://raw.githubusercontent.com/hongwenjun/vps_setup/master/img/youtube.png)频道](https://www.youtube.com/sRGB18/videos) &nbsp;&nbsp;www.youtube.com/sRGB18 &nbsp;&nbsp;[![](https://raw.githubusercontent.com/hongwenjun/vps_setup/master/img/paypal.png)赞赏支持!](https://paypal.me/sRGB18)&nbsp;&nbsp;https://paypal.me/sRGB18
- 推荐新手两个性价比:100:好按时计费VPS: :+1: [vultr.com](https://www.vultr.com/?ref=7425413) :+1: [skysilk.com](https://www.skysilk.com/ref/Xmr9xL1Bnf) 　:+1:按需开启，不用不浪费！
----

- :gift: 项目: https://git.io/vps.us 　　 https://git.io/winkcp 　　 https://git.io/vps.english
- :bomb: 脚本: https://git.io/vps.sh 　　 https://git.io/wgmtu 　　 https://git.io/v2ray.ss
- :anger: 防火墙脚本: https://git.io/fhUSe 　　 路由器脚本: https://git.io/sskcp.sh
- English Script: https://git.io/vps.setup 　　 https://git.io/wireguard.sh 　　 https://git.io/v2ray_ss.sh

---
### :heart_eyes:Linux 简单命令工具和简易脚本
<details>
<summary>点击展开内容</summary>

 ## XPath Helper 简单使用方法
```
1.开启插件 (ctrl+shif+x)
2.鼠标移动到一个标题上方
3.按 shift 键，提取xpath
4.删除xpath尾部[方括号]
  
/a 链接文件    /a/@href  链接地址
  
/html/body[@class='home  pace-done']/section[@class='container']/div[@class='content-wrap']/div[@class='content']/article[@class='excerpt']/header/h2/a/@href
```

## grep ip 并计数
```
grep -oE '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' | sort | uniq -c| sort -nrk 1

# 应用: 统计自己电信服务商IP动态变化
cat /var/log/udp2raw.log \
  | grep -oE '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' | sort | uniq -c| sort -nrk 1

# 统计哪些IP在扫描你的vps
cat /var/log/auth.log \
  | grep -oE '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' | sort | uniq -c| sort -nrk 1

# 查询IP信息
https://www.ipip.net/ipquery.html
```



#### 一些表情例子 EMOJI
- :smile: :laughing: :dizzy_face: :sob: :cold_sweat: :sweat_smile:  :cry: :triumph: :heart_eyes: :relieved:
- :+1: :-1: :100: :clap: :bell: :gift: :question: :bomb: :heart: :coffee: :cyclone: :bow: :kiss: :pray: :anger:

```c
:smile: :laughing: :dizzy_face: :sob: :cold_sweat: :sweat_smile:  :cry: :triumph: :heart_eyes: :relieved:
:+1: :-1: :100: :clap: :bell: :gift: :question: :bomb: :heart: :coffee: :cyclone: :bow: :kiss: :pray: :anger:
```

### 安装工具 tmux 和 fish 等

```
apt install tmux fish  -y
```
### GCP_AZ_AWS_Virmach等小内存优化，htop 或者  systemctl查看有的任务
```
systemctl | grep running

systemctl disable   google-accounts-daemon.service
systemctl disable   google-clock-skew-daemon.service
systemctl disable   google-network-daemon.service
systemctl disable   google-osconfig-agent.service

systemctl disable  unattended-upgrades.service
systemctl disable  fail2ban
systemctl disable  rsyslog
systemctl disable  cron
systemctl disable  getty@tty2.service
systemctl disable  console-getty.service
```

### 微软B1ls 内存只给420M运行Docker崩溃只好开虚拟内存
```
# WALinuxAgent (waagent) 卸载
systemctl disable walinuxagent

# Swap 交换空间

fallocate -l 1G /swapfile
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile

echo "/swapfile swap swap defaults 0 0"  >>  /etc/fstab


# 其他优化设定
vim /etc/sysctl.conf

vm.min_free_kbytes = 18600
vm.swappiness = 5

sysctl -p


网上找了文章  《Azure 乞丐版 B1ls 的正确使用姿势 压榨极致性能》
先凑合着用吧，反正是备用机，续签的 99刀应该可以用一年
----------------
## crontab -l
1   *   */7  *  *   reboot
59  *    *   *  *    wget -qO- git.io/fxxlb | bash
8  */8   *   *  *   docker run --rm  hostloc  用户 密码
```

### 在Android手机上安装Termux应用，测试学习10个秘密和酷命令!

```
1) apt install sl
     sl
2) factor "Any Number"
3) apt install fish
     fish
4) apt install figlet
     figlet "Any Text"
5) apt install cmatrix
     cmatrix
6) apt install fortune
     fortune
7) apt install toilet
     toilet "Any Text"
     toilet -f mono12 -F gay "Any Text"
8) apt install w3m
     w3m "any websites"
     example:- w3m google.com
9) ifconfig
10) apt install cowsay
      cowsay "Any Text"
```

### [acme协议从letsencrypt生成免费的证书](http://srgb.vicp.net/2018/11/05/acme_sh/)

```
#!/usr/bin/env sh

# https://github.com/Neilpang/acme.sh/wiki/说明

# 安装ssl依赖 和 acme.sh工具
apt-get install socat netcat -y
curl  https://get.acme.sh | sh

# 设置域名
DOMAIN=ssl.srgb888.ga

# 生成域名ssl证书
~/.acme.sh/acme.sh  --issue -d ${DOMAIN}  --webroot  /var/www/html --standalone -k ec-256 --force

```

### 如果你用的nginx服务器，以后可以使用一行命令更新证书
```
~/.acme.sh/acme.sh  --issue -d ssl.srgb888.ga  --nginx  --standalone -k ec-256 --force
```

## Linux 使用代理 加速git 和安装软件

```
#!/bin/bash
# socks5tohttp.sh

brook socks5tohttp -s 127.0.0.1:1080 -l 0.0.0.0:8010 &
ps aux | grep -E brook

export http_proxy="http://127.0.0.1:8010"
export https_proxy="http://127.0.0.1:8010"
```
- Windows 系统脚本  VPN --> socks5 --> http代理 给手机使用
```
::  Brook 开启 socks5  再转http
start /b  brook socks5 -l :1080 -i 0.0.0.0
sleep 1
start /b  brook socks5tohttp -s 127.0.0.1:1080 -l 0.0.0.0:8010
```

## 安装 brook 用来 Socks5 转 HTTP 代理
- brook 其他更多使用方法访问 [官方网站](https://txthinking.github.io/brook/#/zh-cn/brook-socks5tohttp)
```
$ curl -L https://github.com/txthinking/brook/releases/download/v20200909/brook_linux_amd64 -o /usr/bin/brook
$ chmod +x /usr/bin/brook

# 32位系统安装
$ curl -L https://github.com/txthinking/brook/releases/download/v20200909/brook_linux_386 -o /usr/bin/brook

```
- Socks5 转 HTTP 代理
```
$ brook socks5tohttp -s 127.0.0.1:1080  -l 127.0.0.1:8010
```

- 中继: 可以将地址中继到远程地址。 它可以中继任何tcp和udp服务器
```
$ brook relay -f :9999 -t 1.2.3.4:9999
```

- brook socks5  运行一个独立的标准socks5服务器（TCP和UDP）
```
$ brook socks5 -l :1080 -i 0.0.0.0
```

## Linux 让终端走代理的几种方法
- https://zhuanlan.zhihu.com/p/46973701


### ssh保持长连接的方式，方法有以下三种：

```
1.修改server端的etc/ssh/sshd_config

ClientAliveInterval 60 ＃server每隔60秒发送一次请求给client，然后client响应，从而保持连接
ClientAliveCountMax 3 ＃server发出请求后，客户端没有响应得次数达到3，就自动断开连接，正常情况下，client不会不响应

systemctl reload sshd

2.修改client端的etc/ssh/ssh_config添加以下：（在没有权限改server配置的情形下）

ServerAliveInterval 60 ＃client每隔60秒发送一次请求给server，然后server响应，从而保持连接
ServerAliveCountMax 3  ＃client发出请求后，服务器端没有响应得次数达到3，就自动断开连接，正常情况下，server不会不响应

3.在命令参数里ssh -o ServerAliveInterval=60 这样子只会在需要的连接中保持持久连接， 毕竟不是所有连接都要保持持久的
```


</details>

---
### Docker 版 RISC-V 交叉编译器和执行 riscv-pke 的环境 [在线阅读](https://262235.xyz/index.php/archives/1250/)
### Hugo编译 C语言入门教程文档 Html静态网站制作 [在线阅读](https://262235.xyz/index.php/archives/1247/)
### Xshell 7 操作 Docker Python3 学习编程 [在线阅读](https://www.262235.xyz/index.php/archives/431/)
### Linux Command 命令大全 [命令列表 离线包](https://262235.xyz/index.php/archives/313/)
### 公益中小学教学视频 - 免费观看  [在线阅读](https://262235.xyz/index.php/archives/216/)
### 旧手机烂手机不要换锈钢脸盆，安装Linux Deploy做移动服务器  [在线阅读](https://262235.xyz/index.php/archives/193/)
### 群晖NAS部署自动PT工具 感谢大神TaterLi  [在线阅读](https://262235.xyz/index.php/archives/119/)
### 一键 WordPress 博客安装脚本，同时也是 LNMP 套件 [在线阅读](https://262235.xyz/index.php/archives/124/)
### 宇宙第一大站 IPT 刷上传，守株待兔也能活 [在线阅读](https://262235.xyz/index.php/archives/86/)
### Typecho 自用博客笔记安装 [上篇](https://262235.xyz/index.php/archives/61/)  [下篇:Typecho-theme-DUX 主题安装](https://262235.xyz/index.php/archives/74/)
### Oracle VM VirtualBox  安装虚拟机 Debian 10  挖坑填坑笔记 [在线阅读](https://github.com/hongwenjun/vps_setup/tree/remove/debian)
### Arch Linux 安装简易版 For VirtualBox 安装虚拟机 填坑笔记 [在线阅读](https://github.com/hongwenjun/vps_setup/blob/remove/Arch/README.md)
### 黑五变态机有救，可以用NFS挂载一个僚机 [在线阅读](https://github.com/hongwenjun/vps_setup/blob/remove/debian/nfsdir.md)
---
### 网友视频和白话文档

- 白话文档: [OpenWRT配置](https://git.io/wrt.wg) 　 [Nginx反代V2ray原理](https://git.io/v2ray.nginx) 　 [rclone使用教程](https://github.com/hongwenjun/vps_setup/blob/master/rclone/README.md) 　 [Debian 安装Transmission教程和一键脚本](https://github.com/hongwenjun/vps_setup/blob/master/rclone/transmission.md)
- 网友视频: [三剑客](https://youtu.be/BHZhU8wxf9A) 　 [PC_MAC_手机客户端](https://youtu.be/dkXWicxak3w)

### Debian 10 Buster 管理员手册  [在线阅读](https://debian-handbook.info/browse/zh-CN/stable/)

- Debian 开发者和 Debian 手册作者 Raphaël Hertzog 宣布面向 Debian 11 的最新版本 Debian 管理员手册已上线。

---


