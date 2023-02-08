RK3588 Mainline U-Boot instructions
==============================

We have a working tree which is very close to mainline and periodically updated. \
It holds the current work in progress patches for rk3588 as well as the \
patches that Collabora has sent upstream. \
The tree is available [here](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/u-boot)

In mainline, there are currently two patchsets adding rk3588 support. \
One is from Rockchip and is based on their downstream kernel headers and one \
is from Jagan Teki and based on the mainline headers:

 * [Rockchip](https://lists.denx.de/pipermail/u-boot/2023-January/506051.html)
 * [Jagan Teki](https://lists.denx.de/pipermail/u-boot/2023-January/506156.html)

A patch adding the ROCK 5B in a minimal configuration by @ehristev was sent upstream:

 * [Board patch][https://lists.denx.de/pipermail/u-boot/2023-February/508039.html]


Current branches
==============================
| Branch Name              | Status                                                                                     | What works ?                                     |
| ------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------ |
| RADXA+USB                | Contains downstream Uboot + USB fixes to have networking operational on USB dongle.        | Everything downstream + USB and Ethernet dongle. |
| 2023.04-rc1-rock5b       | Working branch based on 2023.04-rc1                                                        | Dropping to U-boot prompt.                       |


Current upstream status
==============================
|                          | Phabricator                                    | Branch                | Status                |
| ------------------------ | ---------------------------------------------- | --------------------- | --------------------- |
| Getting the board upstream   | [T40365](https://phabricator.collabora.com/T40365) | 2023.04-rc1-rock5b | Initial patch for the board [sent](https://lists.denx.de/pipermail/u-boot/2023-February/508039.html) |
| Booting from SD-Card     |                                                | 2023.04-rc1-rock5b | Kernel crashes very early with SError irq, not working. Memory ranges which are at fault are 0x3fc000000-0x3fc500000 and 0x3fff00000-0x3ffffffff |
| USB host                 |                                                | 2023.04-rc1-rock5b | INNO PHY is out of date, does not support rk3588, have to forward port from radxa uboot |
| USB Ethernet Dongle      |                                                | | Not attempted as USB Host fails |
| eMMC                     |                                                | | Not attempted at the moment |
| Builtin network          |                                                | | Not attempted at the moment |
| U-boot SPL               |                                                | 2023.04-rc1-rock5b | SPL works, it can load U-boot proper from the SD-Card |



How to build U-boot for rock-5b in 2023.04-rc1-rock5b
==============================

## Prerequisites

### DDR init blob

You need the DDR init blob. \
This comes from [radxa rkbin repository](https://github.com/radxa/rkbin.git) \
and it's named /bin/rk35/rk3588_ddr_lp4_2112MHz_lp5_2736MHz_v1.08.bin

You need to download this file and copy it to the top U-boot sources dir, \
and rename it to `ddr.bin`

### BL31

You need the BL31 ATF. \
This comes from [radxa rkbin repository](https://github.com/radxa/rkbin.git) \
and it's named /bin/rk35/rk3588_bl31_v1.34.elf

You need to download this file and copy it to the top U-boot sources dir, \
and rename it to `atf-bl31`


## Building

 > make rock5b-rk3588_defconfig

And then,

 > make

## Writing binaries to SD-Card for booting from SD-Card

This small tutorial is written for the case when you want to write the boot \
media using your laptop, not when the target has booted into a previous Linux \
installment. \
Insert your SD-Card into your host laptop/workstation. \
Once inserted your SD-Card will be available in your Linux host as \
`/dev/mmcblkX` , let's assume it's `/dev/mmcblk0` further on. \
If you have USB card reader, it will be detected as `/dev/sdX`.

### idbloader.img

This is the miniloader, it must be written to the media like this:
 > dd if=idbloader.img of=/dev/mmcblk0 seek=64

### u-boot.itb

This is the U-boot proper with the ATF images, it must be written to the media \
like this:
 > dd if=u-boot.itb of=/dev/mmcblk0 seek=16384


