---
title:  Ubuntu关机后Nvidia驱动坏了
published: true
category: work
tag: work
---

## 问题

点击关机关闭速度很快，显卡还在运转，导致驱动坏，引发登陆不上循环登陆的问题。

## 日志

家目录下 .xsession_error 
openConnection: connect: 没有那个文件或目录
cannot connect to brltty at :0

## 解决方法

Ctrl+Alt+F1

发现安装后驱动文件并没有删掉，这就好办了。

```
sudo apt-get remove --purge nvidia*
```

```
sudo service lightdm stop
```

```
sudo ./NVIDIA-Linux-x86_64-430.50.run
```

```
sudo service lightdm start
```

解决

## 注意

以后等显卡完全关了，再关机。


## 其他问题

帧率突然不如之前高了，一直没找到原因，难道是让显卡跑了一晚上累着了吗？