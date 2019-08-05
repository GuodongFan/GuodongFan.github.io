---
title: 训练YOLOv3
published: true
category: work
tag: YOLO
---

## 挂载数据盘

```
root@plusai:/# df -l
Filesystem     1K-blocks    Used Available Use% Mounted on
udev            16449300       0  16449300   0% /dev
tmpfs            3294676    4272   3290404   1% /run
/dev/vda1       41152812 9050828  30198328  24% /
tmpfs           16473372     116  16473256   1% /dev/shm
tmpfs               5120       0      5120   0% /run/lock
tmpfs           16473372       0  16473372   0% /sys/fs/cgroup
tmpfs            3294676      20   3294656   1% /run/user/111
tmpfs            3294676       0   3294676   0% /run/user/0
```

```
root@plusai:/# fdisk -l
Disk /dev/vda: 40 GiB, 42949672960 bytes, 83886080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe2eb87fa

Device     Boot Start      End  Sectors Size Id Type
/dev/vda1  *     2048 83886046 83883999  40G 83 Linux


Disk /dev/vdb: 300 GiB, 322122547200 bytes, 629145600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

首先设置文件格式
mkfs.ext4 /dev/vdb

创建要挂载到的目录
mkdir /data

挂载
mount -t ext4 /dev/vdb /data

需要分区
fdisk /dev/sdb
进入分区命令行后，输入n 建立分区，输入p进行主分区，输入1 只分一个分区。进行完成后，输入w写入分区并退出.

开机自动挂载
vi /etc/fstab
/dev/sdb        /data   ext4    defaults        0       2

检查
mount -a

## cudnn

默认安装了cuda查看版本
cat /usr/local/cuda/version.txt

下载cudnn
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
下载地址 https://developer.nvidia.com/rdp/cudnn-archive
cuDNN v7.1.3 Library for Linux

安装cudnn
tar -zxvf cudnn文件名 解压cudnn的文件，然后执行下面命令，注意你的当前路径一定是在cudnn的文件同目录
sudo cp cuda/include/cudnn.h /usr/local/cuda/include/
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64/
sudo chmod a+r /usr/local/cuda/include/cudnn.h
sudo chmod a+r /usr/local/cuda/lib64/libcudnn*

## 安装conda
下载
wget https://repo.anaconda.com/archive/Anaconda3-2019.07-Linux-x86_64.sh

安装后激活
source ~/.profile

## 配置环境

安装git
sudo apt-get install git

使用git下载darknet
git clone https://github.com/pjreddie/darknet

下载预训练文件
wget https://pjreddie.com/media/files/yolov3.weights

## 为什么选择YOLOv3
RCNN族，最先进的MASK RCNN速度太慢，不能满足real time。因此，在公司项目中选定YOLOv3做目标检测。

## 标注工具

MASK RCNN 用http://www.robots.ox.ac.uk/~vgg/software/via/via_demo.html这个网页进行标注即可。

YOLOv3没有延用一些标注标准，作者自己开发了个标注工具，yolo_mark。ps:你用现有数据标准自己开发个工具多好，造福大众多好啊。

## 训练原因

YOLOv3可以识别的物体种类虽然比较多，本项目只需要识别出人就可以，并想通过YOLOv3识别出的行人，进行目标跟踪，实时的检测行人的运动状态。然而，在摔倒等过程中，提供的模型检测率并不好，因此需要加入行人的一些其他的状态去重新训练这个模型。

## 修改makefile使支持GPU

darknet/MakeFile文件
1. GPU=0 --> GPU=1
2. CUDNN=0 --> CUDNN=1
3. DEBUG=0 --> DEBUG=1
4. NVCC=/usr/local/cuda/cuda/bin/nvcc
--> NVCC=/usr/local/cuda-9.1/bin/nvcc
5. COMMON+= -DGPU -I/usr/local/cuda/include
-->COMMON+= -DGPU -I/usr/local/cuda-9.1/include
6. LDFLAGS+= -L/usr/local/cuda/lib64-lcuda -lcudart -lcublas -lcarand
--> LDFLAGS+= -L/usr/local/cuda-9.1/lib64-lcuda -lcudart -lcublas -lcarand

## 查看GPU使用量
每10秒刷新一次
watch -n 10 nvidia-smi
