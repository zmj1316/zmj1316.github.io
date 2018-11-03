---
layout: post
title: 给 Acadia 加上 wifi 模块实现热点 
description: "嵌入式 "
category: tutorial
tags: [Acadia, pcDuino, kernel, WIFI]
imagefeature:
comments: true
share: true
---

嵌入式要用到就简单写一下，主要是内核模块交叉编译的问题

<!--more-->

文章主要参考[这篇博客](http://blog.csdn.net/sumang_87/article/details/38168877)，自己添加了一些交叉编译的内容，
用的 wifi 硬件是很久以前参加活动送的小米随身 wifi 。

### 准备工作：

* Acadia 的内核源码，用于内核模块编译
* 从[github](https://github.com/eywalink/mt7601u)下载用于 mt7601u 的内核模块驱动

### 编译：

这里我假设你已经完成了上一篇讲过的 Acadia 内核编译和内核模块编译

解压内核模块到任意正常的目录，打开目录下的 /src/Makefile ，注释第 32 行的`PLATFORM = PC`：

```
#PLATFORM: Target platform
#PLATFORM = PC
#PLATFORM = 5VT
```

取消 51 行 `PLATFORM = SMDK` 的注释：

```
#PLATFORM = CMPC
#PLATFORM = RALINK_2880
#PLATFORM = RALINK_3052
PLATFORM = SMDK
#PLATFORM = RMI
#PLATFORM = RMI_64
```

找到 270 行附近的 `ifeq ($(PLATFORM),SMDK)`, 修改如下：

```
ifeq ($(PLATFORM),SMDK)
# 下面分别是上次编译内核时使用的 内核 和 交叉编译工具链 的路径
LINUX_SRC = /home/demo/linux-kernel-acadia1.0-beta-master/linux-kernel-acadia1.0-beta/
CROSS_COMPILE=~/fsl-linaro-toolchain-master/bin/arm-fsl-linux-gnueabi-

endif
```

然后在内核模块根目录执行
```
make ARCH-arm
```
进行编译

### 加载

复制在 /src/os/linux 下的 3 个内核模块，以及 `/etc` 目录到 Acadia 上， 将 `/etc/Wireless/RT2870AP/` 
下的所有 .dat 移动到 Acadia 的 `/etc/Wireless/RT2870AP/` 目录下（需要自己创建），根据[这篇博客](http://blog.csdn.net/sumang_87/article/details/38168877) 自己加载配置。

至此关于交叉编译的部分就搞定了，剩下的自己看博客解决吧！
