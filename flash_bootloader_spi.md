# :exclamation: :zap: :exclamation: :zap: This tutorial is obsoleted and it was created for the downstream U-boot by RADXA. Currently the upstream U-boot that we use has a complete tutorial on how to build and flash [here](/upstream_uboot.md)</font>

# Easy flashing the bootloaders on Radxa Rock 5B board's SPI flash (obsoleted, for reference on RADXA's Uboot)

This is a small summary regarding the Radxa Rock5b rk3588 SPI flashing.

This is based on Radxa wiki : \
https://wiki.radxa.com/Rock5/install/spi \
...and it's not exhaustive, it's a small summary

# Step 1
Download artifacts from \
https://gitlab.collabora.com/hardware-enablement/rockchip-3588/u-boot/-/pipelines/latest?ref=RADXA%2BUSB

On the down side , there is a section named `Jobs` with a `download` \
button on the right side for each successful job. \
The artifacts are available from there.

The artifacts are based on branch RADXA+USB. This U-boot supports network \
boot by using a USB Ethernet dongle, and it's based on downstream U-boot \
from Radxa.

# Step 2
You will need rkdevelopment tool. \
Debian users can install `rkdeveloptool` from the package repository. \
A general guide is available here, follow Linux install: \
https://wiki.radxa.com/Rock5/install/rockchip-flash-tools \
After this step you should have three files and `rkdeveloptool` installed :

```
 -rw-r--r-- 1 eugen eugen  284672 Jan 31 16:05 idblock.bin
 -rw-r--r-- 1 eugen eugen  448960 Jan 31 16:05 rk3588_spl_loader_v1.08.111.bin
 -rw-r--r-- 1 eugen eugen 4194304 Jan 31 16:05 uboot.img
```

# Step 3
Hold the maskrom button pressed, then power up the board using USB type C \
cable connected to your laptop, and release the maskrom only after the board \
powered up.

# Step 4
This will download a dedicated SPI tool to the board itself:

```
 # sudo rkdeveloptool db rk3588_spl_loader_v1.08.111.bin
 Downloading bootloader succeeded.
```

# Step 5
Write the idblock.bin at address 0:

```
 # sudo rkdeveloptool wl 0 idblock.bin
 Write LBA from file (100%)
```

# Step 6
Write the U-boot FIT at address 16384:

```
 # sudo rkdeveloptool wl 16384 uboot.img
 Write LBA from file (100%)
```

# Step 7
Reboot the board using rkdeveloptool:

```
 # sudo rkdeveloptool rd
 Reset Device OK.
```


