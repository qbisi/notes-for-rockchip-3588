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
| 2024.01-rk3588           | Working branch based on 2024.01                                                            | Rock-5B: SD-Card, eMMC, SPI Flash, Kernel boot from SD-Card/eMMC/network/DFU, USB Host 2.0/3.0 (storage + Ethernet dongle), USB 3.0 gadget on type C (one orientation only in U-boot proper, both orientations in SPL), pciExpress, rtl8125b in 100 Mbps mode, built-in network in 1000 Mbps mode. Can load SPL with rockusb, then load proper from SD-Card/eMMC/SPI flash/DFU gadget. Rock-5A: board boots from SD-Card. |
| rk3588                   | Mirror of the latest upstream + work in progress development                               | Currently mirroring 2024.01-rk3588 |


Current upstream status
==============================
|                          | Phabricator                                        | Branch                | Status                |
| ------------------------ | -------------------------------------------------- | --------------------- | --------------------- |
| Initial SoC support      | n/a                                                | 2024.01-rk3588    | included in upstream  |
| Initial Rock 5B support  | [T40365](https://phabricator.collabora.com/T40365) | 2024.01-rk3588    | included in upstream  |
| Faulty memory ranges     |                                                    | 2024.01-rk3588    | included in upstream. Memory ranges which are at fault are 0x3fc000000-0x3fc500000 and 0x3fff00000-0x3ffffffff |
| Booting from SD-Card     |                                                    | 2024.01-rk3588    | Works |
| Booting from SPI flash   | [T41315](https://phabricator.collabora.com/T41315) | 2024.01-rk3588    | Works |
| Booting from eMMC        | [T41154](https://phabricator.collabora.com/T41154) | 2024.01-rk3588    | Works |
| USB host 2.0             | [T40661](https://phabricator.collabora.com/T40661) | 2024.01-rk3588    | INNO PHY has basic support (no tuning, no OTG) USB 2.0 host works. |
| USB host 3.0             | [T42194](https://phabricator.collabora.com/T42194) | 2024.01-rk3588    | USB 3.0 host works (DWC3 controller + USBDP PHY) |
| USB gadget 3.0           | [T42194](https://phabricator.collabora.com/T42194) | 2024.01-rk3588    | Works with one orientation in 2.0 mode at the type C controller |
| USB gadget 3.0 in SPL    | [T42194](https://phabricator.collabora.com/T42194) | 2024.01-rk3588    | Works with both orientations in 2.0 mode with DWC3 patches. DWC3 needs a resync to be able to upstream these [T43165](https://phabricator.collabora.com/T43165) |
| USB type C               | [T42194](https://phabricator.collabora.com/T42194) | 2024.01-rk3588    | type C stack and fusb driver requires porting, working at the moment in gadget mode in one orientation only |
| USB Ethernet Dongle      |                                                    | 2024.01-rk3588    | Works with USB 2.0/3.0 support |
| SPI                      | [T41315](https://phabricator.collabora.com/T41315) | 2024.01-rk3588    | Works |
| PMIC                     |                                                    |                   | Not attempted at the moment |
| USB PD Controller        |                                                    |                   | Not attempted at the moment |
| PCIe v2 Host Controller  | [T41351](https://phabricator.collabora.com/T41351) | 2024.01-rk3588    | Works, required for external RTL8125B network |
| RTL8125B network(PCIe)   | [T41351](https://phabricator.collabora.com/T41351) | 2024.01-rk3588    | Works in 100 Mbps mode |
| Builtin network          | [T43981](https://phabricator.collabora.com/T43981) |                   | Works |
| U-boot SPL               |                                                    | 2024.01-rk3588    | SPL works, it can load U-boot proper from the SD-Card/eMMC/SPI flash, even if loaded via rockusb |
| U-boot SPL DFU gadget    |                                                    | 2024.01-rk3588    | Works, when loaded with rockusb, it will start DFU gadget and can download u-boot proper via DFU |

How to build U-boot for rock-5b in 2024.01-rk3588
==============================

## Prerequisites

You will have to clone or download the rkbin Rockchip binary blob repository from [here](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/rkbin.git) \
You also need the Trusted-Firmware-A repo from [here](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/trusted-firmware-a) \
Assume you have a top dir and then \
-. \
├── rkbin \
├── u-boot \
├── trusted-firmware-a

### Rockchip TPL (ddr init blob)

You need the Rockchip TPL (DDR init blob), which is in the rkbin repo, and needs \
to be passed to U-boot.

### BL31

You need the BL31 ATF, which must be built from the trusted-firmware-a repo, and needs \
to be passed to U-boot.

#### Building BL31

 > cd trusted-firmware-a

And then,

 > make PLAT=rk3588 bl31

## Building

 > cd u-boot

Export variables pointing to the required files from rkbin and trusted-firmware-a:

 > export ROCKCHIP_TPL=../rkbin/bin/rk35/rk3588_ddr_lp4_2112MHz_lp5_2736MHz_v1.08.bin

 > export BL31=../trusted-firmware-a/build/rk3588/release/bl31/bl31.elf

Build the config:

 > make rock5b-rk3588_defconfig

And then,

 > make

Note that the building process and the binaries are the same, regardless \
of the boot media you decide to use further on.

## Building the rockchip loader binaries

To later flash binaries on the board, you will need a special loader binary.

To build this binary, follow the steps:

 > cd ../rkbin/
 > ./tools/boot_merger RKBOOT/RK3588MINIALL.ini

you should get this output:

```
********boot_merger ver 1.2********`
Info:Pack loader ok.
```
and the obtained binary file is named `rk3588_spl_loader_v1.08.111.bin`

Writing binaries to SD-Card for booting from SD-Card
==============================

## Introduction

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

Writing binaries to SPI flash/eMMC for booting from SPI flash/eMMC
==============================

This small tutorial is written for the case when you want to write the boot \
media using your laptop with flashing tools, not when the target has booted \
into a previous Linux installment.

***Note*** that if you have an eMMC module inserted in the board, \
***this*** module is written/erased by using the below procedure. \
It appears rockchip does not allow you to select the `flash` device, \
but rather decides on its own which flash to write/erase, and the one \
that has priority is the eMMC. If there is no eMMC found, then the \
SPI flash is written/erased. \
Hence if you want to erase/write the SPI flash, you have to ***remove*** \
the eMMC add-on board.

***Note*** that considered the above, writing binaries on either the \
SPI flash or eMMC is similar, differences are pointed below.

## Prerequisites
To flash the memories on the board, a special loader tool is required. \
This can be either built from `rkbin` tree downloaded at the build stage, \
as described in the build section, or it can be downloaded from our \
CI artifacts page [here](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/u-boot/-/pipelines/latest?ref=rk3588-rock5b)

You will also need rkdevelopment tool. \
This tool will interact with the rk3588 SoC using USB in maskrom mode. \
Debian users can install `rkdeveloptool` from the package repository. \
A general guide is available here, follow Linux install: \
https://wiki.radxa.com/Rock5/install/rockchip-flash-tools \

## Step 1
Once you build your artifacts, and have the prerequisites, \
you will use `rk3588_spl_loader_v1.08.111.bin` which is the loader that \
and interacts with the SPI flash/eMMC.

## Step 2
After this step you should have five files and `rkdeveloptool` installed :

```
 -rw-r--r-- 1 eugen eugen  284672 Jan 31 16:05 idbloader.img
 -rw-r--r-- 1 eugen eugen  448960 Jan 31 16:05 rk3588_spl_loader_v1.08.111.bin
 -rw-r--r-- 1 eugen eugen 4194304 Jan 31 16:05 u-boot.itb
 -rw-rw-r-- 1 eugen eugen 9467904 Apr 28 16:59 u-boot-rockchip.bin
 -rw-rw-r-- 1 eugen eugen 1506816 May 19 12:59 u-boot-rockchip-spi.bin
```

***u-boot-rockchip.bin*** is just a concatenation of idbloader.img and u-boot.itb \
at the correct offsets so it can be written in one go, dedicated for eMMC device. \
***u-boot-rockchip-spi.bin*** is a similar file for SPI flash.

## Step 3
Hold the maskrom button pressed, then power up the board using USB type C \
cable connected to your laptop, and release the maskrom only after the board \
powered up. \
More information about how to enter maskrom mode is available [here](rock5b-maskrom-automation.md)

## Step 4
This will download the dedicated flashing tool to the board itself:

```
 # sudo rkdeveloptool db rk3588_spl_loader_v1.08.111.bin
 Downloading bootloader succeeded.
```

## Step 5 for SPI flash only
This will erase the SPI flash: (works also for eMMC, but you may have \
user partitions on eMMC, so ***don't do this unless you know what you are doing***)
```
  # sudo rkdeveloptool ef
Starting to erase flash...
```

***Note:*** After this step you need to reset the board again into maskrom mode. \
and redo Step 4.

## Step 6 for SPI flash only
Write the u-boot-rockchip-spi.bin at sector 0:
```
 # sudo rkdeveloptool wl 0 u-boot-rockchip-spi.bin # SPI flash
 Write LBA from file (100%)
```

## Step 6 for eMMC only
Write the u-boot-rockchip.bin at sector 64:
```
 # sudo rkdeveloptool wl 64 u-boot-rockchip.bin # eMMC
 Write LBA from file (100%)
```

## Step 7
Reboot the board. \
You are done, the board should boot from SPI flash/eMMC now. \
***Note*** that SPI flash/eMMC takes precedence over SD-Card. To boot again from \
SD-Card you need to erase the flash and/or remove the eMMC.

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
The SPL will try to load the image for U-boot proper with DFU after it starts.

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


How to load u-boot proper (u-boot.itb) using DFU at SPL stage
==============================

Once you create the DDR blob + SPL and boot it, the SPL will attempt \
to boot from DFU.

On the host side, you need `dfu-util` package, which can be installed \
directly from your distribution's package manager.

When SPL starts, it will print out this message:
 > Trying to boot from DFU

At this moment on the host you can do:
```
 # dfu-util -l
```

You should see something similar with:
 > Found DFU: [2207:350b] ver=0223, devnum=80, cfg=1, intf=0, path="6-2", alt=0, name="u-boot.itb", serial="UNKNOWN"

Then, to load U-boot proper:
```
 # dfu-util -a 0 -D u-boot.itb -R
```

After this step, the downloaded U-boot proper should boot normally.
