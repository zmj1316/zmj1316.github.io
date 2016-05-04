---
layout: post
title: How to flash u-boot.bin into acadia
description: "嵌入式 "
category: tutorial
tags: [Acadia, pcDuino, u-boot]
imagefeature:
comments: true
share: true
---
嵌入式用的是 `Acadia` ，自带一块 emmc 但是很难搞，折腾了一下才把 u-boot 刷进去。

<!--more-->
* 1.	From https://github.com/linksprite/u-boot-acadia1.0-beta download u-boot source code for Acadia.
* 2.	Install arm cross compile tools
* 3.	Run:

~~~
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- distclean
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- mx6q_sabresd_config
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf-
~~~

* 4.	Connect the board and copy uboot.bin into acadia 
* 5.	Disable write protection:

~~~
 #> echo 0 > /sys/block/mmcblk0boot0/force_ro 
~~~

* 6.

~~~	
dd if=u-boot.bin of=/dev/mmcblk0boot0 bs=512 seek=2 skip=2
~~~

* 7.	reboot
