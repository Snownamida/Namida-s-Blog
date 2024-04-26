---
title: Termux折腾
date: 2024-04-26 23:55:57
tags:
 - Termux
 - 折腾
 - 技术
---

要是能在手机里跑一个完整的Linux, 随时随地可以用别的电脑远程桌面到上面, 不久有了一个随身便携的电脑了吗! 还能用它做一些好玩的事情, 比如ffmpeg压缩视频......

<!-- more -->

首先安装的时候不要用Google Play, 那上面的是旧版的. 用Fdroid下载最新版. [Termux | F-Droid - Free and Open Source Android App Repository](https://f-droid.org/zh_Hans/packages/com.termux/)

安装好第一件事情是把sshd安排上, 不然得用手机敲命令行......官方教程在这里: [Remote Access - Termux Wiki](https://wiki.termux.com/wiki/Remote_Access#Using_the_SSH_server)

```bash
pkg up
pkg in openssh
sshd
```

查看当前用户名并设置密码

```bash
whoami
passwd
```
这样就可以在电脑连接了. 默认端口号是8022
接下来的操作就都在电脑上啦

接下来根据[PRoot - Termux Wiki](https://wiki.termux.com/wiki/PRoot#Installing_Linux_distributions)安装进入Ubuntu

```bash
pkg install proot-distro
proot-distro list
proot-distro install ubuntu-lts
proot-distro login ubuntu-lts
```

Emmm一开始想装Ubuntu是希望用它安装KDE, 然后用VNC连接. 但折腾了一圈VNC屏幕一直是灰屏, 暂时放弃这条路子

这里有不用PRoot的图形界面教程[Graphical Environment - Termux Wiki](https://wiki.termux.com/wiki/Graphical_Environment).

```bash
pkg install x11-repo tigervnc mate-* marco
vncserver 
export DISPLAY=":1"
```

修改`~/.vnc/xstartup`为

```bash
#!/data/data/com.termux/files/usr/bin/sh
mate-session &
```

### 杂

Termux的包管理系统[Package Management - Termux Wiki](https://wiki.termux.com/wiki/Package_Management). pkd有很多命令缩写挺好的. 以及有一个命令`termux-change-repo`可以一键换源很nice.

Termux和Linux的关系[Differences from Linux - Termux Wiki](https://wiki.termux.com/wiki/Differences_from_Linux)

在Termux上安装Linux发行版[PRoot - Termux Wiki](https://wiki.termux.com/wiki/PRoot#Installing_Linux_distributions)



