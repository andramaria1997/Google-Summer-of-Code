# Basic booting of IMX8-MM-PICO

Boot board with [`linux-next`](https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/)
The board came with linux kernel version 4.9 installed.
Dependencies: crossbuild-essential-arm64

```console
sudo apt-get install crossbuild-essential-arm64
```

In order to boot linux-next on the board, we need the linux-next image to be in 
FIT (Flattened Image Tree) format (.itb file). You can check type of installed k
ernel image by getting the image file from the board on local machine (e.g: create
a local network and use scp) and then execute the following command on that file:
```console
mkimage -l file
```
This will describe image format. "mkimage" tool is part of U-Boot bootloader, so
 in order to use it, compiling U-Boot is necessary.
Steps for compiling [`U-Boot`](https://github.com/wandboard-org/uboot-imx):

```console
$ export ARCH=arm64
$ export CROSS_COMPILE=/path/to/compiler/
$ make defconfig
$ make -j8
```
Now you have mkimage executable file in uboot-imx/tools/ directory.

How to generate kernel.itb file with kernel Image and .dtb file:
```console
$ mkimage -f kernel.its kernel.itb
```
"kernel.its" file is attached to this repository and it uses the following files:
1. Kernel Image
2. wand-pi-8m.dtb file
3. ramdisk.cpio

All mentioned files need to be in the same directory, or you can change the path
 set by "data" field in kernel.its file for each one of them. The first two file
s are obtained by compiling linux-next and are found in the following directories:

Image: linux-next/arch/arm64/boot/  
wand-pi-8m.dtb file: linux-next/arch/arm64/boot/dts/freescale/  
The third one is [`initrd`](https://developer.ibm.com/articles/l-initrd/) file necessary
for booting.

Steps for compiling linux-next:
```console
$ export ARCH=arm64
$ export CROSS_COMPILE=/path/to/compiler/
$ make defconfig
$ make -j8
```

After compiling, you can obtain kernel.itb using mkimage as mentioned before.

Now, having kernel.itb file, we can boot linux-next on the board. Steps:

1. Create on local machine a tftp directory and put kernel.itb file there
```console
TODO: steps to export tftp directory
```
2. Connect the board and stop it in u-boot mode
3. FIT image will boot from "fit_addr" environment variable. So, load kernel.itb
 obtained file at that address with tfpt by using the following command:
```console
tftp ${fit_addr} kernel.itb
```
4. Boot the image:
```console
$ bootm
```