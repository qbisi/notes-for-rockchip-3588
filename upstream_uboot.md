RK3588 Mainline U-Boot instructions
==============================

We have a working tree which is very close to mainline and periodically updated. \
It holds the current work in progress patches for rk3588 as well as the \
patches that Collabora has sent upstream. \
The tree is available [here](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/u-boot) \
Branches in this tree are described in the table below.

Current branches
==============================
| Branch Name              | Status                                                                                     | What works ?                                     |
| ------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------ |
| RADXA+USB                | Contains downstream Uboot + USB fixes to have networking operational on USB dongle.        | Everything downstream + USB and Ethernet dongle. |
| 2023.04-rc5-rock5b       | Working branch based on 2023.04-rc5                                                        | Dropping to U-boot prompt. SD-Card, Kernel boot from SD-Card, USB Host 2.0 (storage + Ethernet dongle). Can load SPL with rockusb, then load proper from SD-Card. SPI flash does not work correctly |
| rk3588-rock5b            | Mirror of the latest upstream + work in progress development                               | Currently mirroring 2023.04-rc5-rock5b |


Current upstream status
==============================
|                          | Phabricator                                        | Branch                | Status                |
| ------------------------ | -------------------------------------------------- | --------------------- | --------------------- |
| Initial SoC support      | n/a                                                | 2023.04-rc5-rock5b    | included in upstream  |
| Initial Rock 5B support  | [T40365](https://phabricator.collabora.com/T40365) | 2023.04-rc5-rock5b    | included in upstream  |
| Faulty memory ranges     |                                                    | 2023.04-rc5-rock5b    | included in upstream. Memory ranges which are at fault are 0x3fc000000-0x3fc500000 and 0x3fff00000-0x3ffffffff |
| Booting from SD-Card     |                                                    | 2023.04-rc5-rock5b    | Works |
| Booting from eMMC        | [T41154](https://phabricator.collabora.com/T41154) |                       | Not attempted at the moment, different IP from SD-Card |
| USB host                 | [T40661](https://phabricator.collabora.com/T40661) | 2023.04-rc5-rock5b    | INNO PHY has basic support (no tuning, no OTG) USB 2.0 host works. [patch sent](https://lists.denx.de/pipermail/u-boot/2023-March/511274.html) |
| USB Ethernet Dongle      |                                                    | 2023.04-rc5-rock5b    | Works with USB 2.0 support |
| SPI                      | [T41315](https://phabricator.collabora.com/T41315) |                       | Not working, required for PMIC and SPI flash. Reads garbage from SPI flash.|
| PMIC                     |                                                    |                       | Not attempted at the moment |
| USB PD Controller        |                                                    |                       | Not attempted at the moment |
| PCIe v2 Host Controller  |                                                    |                       | Not attempted at the moment, required for built-in network |
| Builtin network          |                                                    |                       | Not attempted at the moment |
| U-boot SPL               |                                                    | 2023.04-rc5-rock5b    | SPL works, it can load U-boot proper from the SD-Card, even if loaded via rockusb |

How to build U-boot for rock-5b in 2023.04-rc5-rock5b
==============================

## Prerequisites

You will have to clone or download the rkbin Rockchip binary blob repository from [here](https://github.com/radxa/rkbin.git) \
Assume you have a top dir and then \
-. \
├── rkbin \
├── u-boot

### Rockchip TPL (ddr init blob)

You need the Rockchip TPL (DDR init blob), which is in the rkbin repo, and needs \
to be passed to U-boot.

### BL31

You need the BL31 ATF, which is in the rkbin repo, and needs
to be passed to U-boot.

## Building

 > cd u-boot

Export variables pointing to the required files from rkbin:

 > export ROCKCHIP_TPL=../rkbin/bin/rk35/rk3588_ddr_lp4_2112MHz_lp5_2736MHz_v1.08.bin

 > export BL31=../rkbin/bin/rk35/rk3588_bl31_v1.28.elf

Build the config:

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

How to create a blob containing DDR init and SPL for rockusb
==============================

## Prerequisites

You will have to clone or download the rkbin Rockchip binary blob repository from [here](https://github.com/radxa/rkbin.git) \
Assume you have a top dir and then \
-. \
├── rkbin \
├── u-boot

You will also need to install the rockusbrs crate from [here](https://github.com/collabora/rockchiprs)

## Purpose

Using the rockchip boot merger, we can create one bin file which will contain \
two binaries: the DDR init blob, and our built SPL. \
Then we can use rockusb protocol to load this binary to the target, \
by first booting in Maskrom mode. \
This way, via USB, we can load a bootloader without depending on any media. \
The SPL will try to boot from any supported media after it's loaded.

**Notice** : boot merger from rockchip is different. It will not work. \
You require the boot merger from radxa repository.

## Booting in maskrom
Please refer to instructions [here](rock5b-maskrom-automation.md)

## Create the binary

 > ../rkbin/tools/boot_merger rock5b-rk3588.ini

you should get this output:

```
********boot_merger ver 1.2********`
Info:Pack loader ok.
```

and the obtained binary file is named `rock5b-rk3588.bin`

## Load the binary

 > rockusb download-boot rock5b-rk3588.bin

you should get this output:

```
0 Name: UsbHead
Done!... waiting 1ms
1 Name: rk3588_ddr_lp4_2112M
Done!... waiting 1ms
0 Name: u-boot-spl
Done!... waiting 0ms
```

There is no need to perform any additional steps, the software should run \
immediately after it's loaded.
