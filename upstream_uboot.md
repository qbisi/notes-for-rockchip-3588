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
| 2023.04-rock5b           | Working branch based on 2023.04 plus the next branch                                       | Dropping to U-boot prompt. SD-Card, SPI Flash, Kernel boot from SD-Card/network, USB Host 2.0 (storage + Ethernet dongle). Can load SPL with rockusb, then load proper from SD-Card or SPI flash. |
| rk3588-rock5b            | Mirror of the latest upstream + work in progress development                               | Currently mirroring 2023.04-rock5b |


Current upstream status
==============================
|                          | Phabricator                                        | Branch                | Status                |
| ------------------------ | -------------------------------------------------- | --------------------- | --------------------- |
| Initial SoC support      | n/a                                                | 2023.04-rock5b    | included in upstream  |
| Initial Rock 5B support  | [T40365](https://phabricator.collabora.com/T40365) | 2023.04-rock5b    | included in upstream  |
| Faulty memory ranges     |                                                    | 2023.04-rock5b    | included in upstream. Memory ranges which are at fault are 0x3fc000000-0x3fc500000 and 0x3fff00000-0x3ffffffff |
| Booting from SD-Card     |                                                    | 2023.04-rock5b    | Works |
| Booting from SPI flash   | [T41315](https://phabricator.collabora.com/T41315) | 2023.04-rock5b    | Works |
| Booting from eMMC        | [T41154](https://phabricator.collabora.com/T41154) |                       | Not attempted at the moment, different IP from SD-Card |
| USB host                 | [T40661](https://phabricator.collabora.com/T40661) | 2023.04-rock5b    | INNO PHY has basic support (no tuning, no OTG) USB 2.0 host works. [patch sent](https://lists.denx.de/pipermail/u-boot/2023-March/511274.html) |
| USB Ethernet Dongle      |                                                    | 2023.04-rock5b    | Works with USB 2.0 support |
| SPI                      | [T41315](https://phabricator.collabora.com/T41315) |                       | Works. Can read/write/erase the SPI flash.|
| PMIC                     |                                                    |                       | Not attempted at the moment |
| USB PD Controller        |                                                    |                       | Not attempted at the moment |
| PCIe v2 Host Controller  |                                                    |                       | Not attempted at the moment, required for built-in network |
| Builtin network          |                                                    |                       | Not attempted at the moment |
| U-boot SPL               |                                                    | 2023.04-rock5b    | SPL works, it can load U-boot proper from the SD-Card and SPI flash, even if loaded via rockusb |

How to build U-boot for rock-5b in 2023.04-rock5b
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

Note that the building process and the binaries are the same, regardless \
of the boot media you decide to use further on.

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

***Note*** that SPI flash booting takes precedence over SD-Card booting. \
So you have to erase the SPI flash if it contains valid booting files.

## Writing binaries to SPI flash for booting from SPI flash

This small tutorial is written for the case when you want to write the boot \
media using your laptop with flashing tools, not when the target has booted \
into a previous Linux installment.

### Step 1
Once you build your artifacts, you will also need one separate file that \
comes from radxa/rockchip, which is a tool that runs on the board and \
interacts with the SPI flash.

This file can be downloaded from [here](https://github.com/radxa/rkbin/blob/master/bin/rk35/rk3588_spl_loader_v1.08.111.bin)

# Step 2
You will need rkdevelopment tool. \
This tool will interact with the rk3588 SoC using USB in maskrom mode. \
Debian users can install `rkdeveloptool` from the package repository. \
A general guide is available here, follow Linux install: \
https://wiki.radxa.com/Rock5/install/rockchip-flash-tools \
After this step you should have three files and `rkdeveloptool` installed :

```
 -rw-r--r-- 1 eugen eugen  284672 Jan 31 16:05 idbloader.img
 -rw-r--r-- 1 eugen eugen  448960 Jan 31 16:05 rk3588_spl_loader_v1.08.111.bin
 -rw-r--r-- 1 eugen eugen 4194304 Jan 31 16:05 u-boot.itb
```

### Step 3
Hold the maskrom button pressed, then power up the board using USB type C \
cable connected to your laptop, and release the maskrom only after the board \
powered up. \
More information about how to enter maskrom mode is available [here](rock5b-maskrom-automation.md)

### Step 4
This will download the dedicated SPI tool to the board itself:

```
 # sudo rkdeveloptool db rk3588_spl_loader_v1.08.111.bin
 Downloading bootloader succeeded.
```

### Step 5
This will erase the SPI flash:
```
  # sudo rkdeveloptool ef
Starting to erase flash...
```

***Note:*** After this step you need to reset the board again into maskrom mode. \
and redo Step 4.

### Step 6
Write the idbloader.img at sector 0:

```
 # sudo rkdeveloptool wl 0 idblock.bin
 Write LBA from file (100%)
```

### Step 7
Write the U-boot FIT at sector 0x400:

```
 # sudo rkdeveloptool wl 0x400 u-boot.itb
 Write LBA from file (100%)
```

***Note:*** rkdeveloptool requires _sectors_ as argument, and one sector is \
512 bytes. Hence 0x400 x 512 = 0x80000 bytes, which is the Uboot configuration \
CONFIG_SYS_SPI_U_BOOT_OFFS

### Step 8
Reboot the board. \
You are done, the board should boot from SPI flash now. \
***Note*** that SPI flash takes precedence over SD-Card. To boot again from \
SD-Card you need to erase the flash.

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
