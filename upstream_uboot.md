RK3588 Mainline U-Boot instructions
==============================

We have a working tree which is very close to mainline and periodically updated. \
It holds the current work in progress patches for rk3588 as well as the \
patches that Collabora has sent upstream. \
The tree is available [here](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/u-boot)

Current branches
==============================
| Branch Name              | Status                                                                                     | What works ?                                     |
| ------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------ |
| RADXA+USB                | Contains downstream Uboot + USB fixes to have networking operational on USB dongle.        | Everything downstream + USB and Ethernet dongle. |
| 2023.04-rc1-rock5b       | Working branch based on 2023.04-rc1                                                        | Dropping to U-boot prompt.                       |


RK3588 Current mainline support
==============================

|                              | Phabricator                                        | Status             |
| ---------------------------- | -------------------------------------------------- | ------------------ |
| Getting the board upstream   | [T40365](https://phabricator.collabora.com/T40365) | Currently there is no support upstream |
