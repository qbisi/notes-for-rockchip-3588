# Rock5B pancsf kernel driver recipe

I kick-started my setup uising a [pre-built image](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/debian-image-recipes/-/pipelines)
from the RK3588 hardware enablement project as a base, and installed
a custom kernel and corresponding firmware on top.

These instructions should help people replicate my setup, which is useful
for Panfrost development.

The custom kernel + firmware is required, because the RK3588 hardware
enablement project does not yet have working Graphics (i.e. neither video
output, nor Panfrost kernel driver).

## Compile and install kernel

- Kernel tree: https://github.com/Googulator/linux-rk3588-midstream
- Branch: pancsf-midstream

Setup based on Debian

```console
$ git clone https://github.com/Googulator/linux-rk3588-midstream -b pancsf-midstream
$ cd linux-rk3588-midstream
```

### Setup the kernel config:

```console
$ cp arch/arm64/configs/rock-5b.config .config
$ ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- make olddefconfig
```

### Cross-compile kernel from x64:

```console
$ ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- make -j$(nproc --ignore=2) KBUILD_IMAGE=arch/arm64/boot/Image bindeb-pkg
```

### Install kernel

Copy to the device using your preferred method. I'm doing scp, because rsync isn't in the base-image, but either should work. 

```console
$ scp ../linux-image-<VERSION>_arm64.deb <user>@<device>:
```

Then install the kernel using `dpkg`:

```console
$ sudo dpkg -i linux-image-<VERSION>_arm64.deb
```

## Install firmware on device:

The firmware can be found here: <https://gitlab.com/rk3588_linux/linux/libmali/-/blob/linux-5.10/firmware/g610/mali_csffw.bin>

Place the file at `/lib/firmware/mali_csffw.bin` on the device.

Set up a hook to copy it into the initramfsm, in `/usr/share/initramfs-tools/hooks/mali_csffw`:

```shell
#!/bin/sh

PREREQ=""

prereqs()
{
	echo "$PREREQ"
}

case $1 in
# get pre-requisites
prereqs)
	prereqs
	exit 0
	;;
esac

. /usr/share/initramfs-tools/hook-functions
mkdir -p ${DESTDIR}/lib/firmware || true
cp -pnL /lib/firmware/mali_csffw.bin ${DESTDIR}/lib/firmware
```

Then make sure the hook is executable, and update the initramfs:

```console
$ chmod a+x /usr/share/initramfs-tools/hooks/mali_csffw 
$ update-initramfs -u
```
