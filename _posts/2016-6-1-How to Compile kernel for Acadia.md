---
layout: post
title: How to compile kernel for Acadia
description: "嵌入式 "
category: tutorial
tags: [Acadia, pcDuino, kernel, cross-toolchain]
imagefeature:
comments: true
share: true
---
Acadia again!

又是 Acadia ，作为一个被生产厂家抛弃的产品还真是不好搞啊！
<!--more-->
### Prepare

* 1.Download kernel from [Here](https://github.com/linksprite/linux-kernel-acadia1.0-beta/)

* 2.Download cross-tool from [Here](https://github.com/embest-tech/fsl-linaro-toolchain/) or you may experience kernel panic

### Compile

You will need `mkimage` to make uImage. You can find it under `tools` in u-boot dir if you have compiled u-boot, 
or you may need something like `uboot-tools` in openSUSE that contains `mkimage`.

It is suggested that you use the [cross-tools](https://github.com/embest-tech/fsl-linaro-toolchain/) above and 
add `/bin` to your path so you don't need to add the path in the `CROSS_COMPILE` field.

Make sure you can access `arm-none-linux-gnueabi-gcc` in kernel root dir, 
or you may have to add the full path to the `CROSS_COMPILE` field.

```
make ARCH=arm CROSS_COMPILE=arm-none-linux-gnueabi- imx6acadia_defconfig

make ARCH=arm CROSS_COMPILE=arm-none-linux-gnueabi- menuconfig

make ARCH=arm CROSS_COMPILE=arm-none-linux-gnueabi- clean

make ARCH=arm CROSS_COMPILE=arm-none-linux-gnueabi- uImage
```

### Burn

If you are using other version of `gcc`, it's suggested that test the new kernel on u-boot through network before burn it into board.

* 1.Copy `uImage` from `arch/arm/boot` to Acadia.

* 2.Burn:

```
dd if=$FILE of=/dev/mmcblk0 bs=1M seek=1 conv=fsync
```

* 3.Reboot

### Modules

Of course you want to compile kernel modules for the new kernel, here is a example of `Makefile`,
you may try to find the `/lib/build` dir, but here you just set the `KERNEL_DIR` to the kernel root dir:


```
obj-m := module.o

KERNEL_DIR := /home/demo/linux-kernel-acadia1.0-beta

PWD := $(shell pwd)
ARGS := ARCH=arm CROSS_COMPILE=arm-none-linux-gnueabi-
all:
    make -C $(KERNEL_DIR) SUBDIRS=$(PWD) $(ARGS) modules
clean:
    rm *.o *.ko *.mod.c
.PHONY:clean
```


### How to flash a blocked Acadia on Windows?
[tutorial-on-flashing-linksprite-acadia](http://learn.linksprite.com/acadia/tutorial-on-flashing-linksprite-acadia/)
