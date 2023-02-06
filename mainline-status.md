RK3588 Mainline U-Boot support
==============================

There is currently two patchsets adding rk3588 support. One is from Rockchip
and is based on their downstream kernel headers and one is from Jagan Teki
and based on the mainline headers:

 * [Rockchip](https://lists.denx.de/pipermail/u-boot/2023-January/506051.html)
 * [Jagan Teki](https://lists.denx.de/pipermail/u-boot/2023-January/506156.html)

RK3588 Mainline Kernel support
==============================

|                          | Phabricator                                        | SoC      | Rock Pi 5A | Rock Pi 5B | EVB1    | Notes |
| ------------------------ | -------------------------------------------------- | -------- | ---------- | ---------- | ------- | ----- |
| PMIC (rk806)             | [T36154](https://phabricator.collabora.com/T36154) | n/a      |            |            |         | https://lore.kernel.org/all/20230127181244.160887-1-sebastian.reichel@collabora.com/
| USB-PD Controller        | [T40098](https://phabricator.collabora.com/T40098) | n/a      |            |            |         |
| cpufreq                  | [T36830](https://phabricator.collabora.com/T36830) |          |            |            | WIP     | EVB1 supported in sre's branch
| PCIe                     | [T39901](https://phabricator.collabora.com/T39901) |          |            |            |         | https://lore.kernel.org/all/5bec43fe-ff81-bc68-7b62-9e605b7e1f42@omnom.net/ , https://lore.kernel.org/all/cover.1675498628.git.wqu@suse.com/
| Ethernet                 | [T35212](https://phabricator.collabora.com/T35212) | 6.1-rc1  | 6.3-rc1    |            | 6.3-rc1 |
| USB 2                    | [T39908](https://phabricator.collabora.com/T39908) |          |            |            |         |
| USB 3                    | [T39908](https://phabricator.collabora.com/T39908) |          |            |            |         | https://github.com/neggles/linux-quartz64/issues/1
| USB-C                    | [T39908](https://phabricator.collabora.com/T39908) |          |            |            |         |
| eMMC                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  | 6.3-rc1    | 6.3-rc1    | 6.3-rc1 |
| SD Card                  | [T39448](https://phabricator.collabora.com/T39448) | ready    | ready      |            |         | Rock 5A supported in sre's branch, waiting for rk806 upstream support
| SDIO                     |                                                    |          |            |            |         |
| SATA                     |                                                    |          |            |            |         |
| Display Controller       |                                                    |          |            |            |         |
| - HDMI Output            | [T36469](https://phabricator.collabora.com/T36469) |          |            |            |         |
| - HDMI Audio             |                                                    |          |            |            |         |
| - DSI Output support     |                                                    |          |            |            |         |
| - DP1.4 USB-C AltMode    |                                                    |          |            |            |         |
| M2 E                     |                                                    |          |            |            |         |
| M2 M                     |                                                    |          |            |            |         |
| Headphone Jack Playback  |                                                    |          |            |            |         |
| Headphone Jack Record    |                                                    |          |            |            |         |
| Real Time Clock (RTC)    |                                                    | n/a      |            |            | 6.3-rc1 |
| HW crypto engine         |                                                    |          |            |            |         | https://lore.kernel.org/all/20220927080048.3151911-1-clabbe@baylibre.com/
| UART                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  | 6.3-rc1    | 6.3-rc1    | 6.3-rc1 |
| GPIO                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  |            |            |         |
| Pinmux                   | [T34481](https://phabricator.collabora.com/T34481) | 5.19-rc1 | n/a        | n/a        | n/a     |
| Interrupts               | [T34481](https://phabricator.collabora.com/T34481) | 6.3-rc1  | n/a        | n/a        | n/a     |
| PWM                      | [T34481](https://phabricator.collabora.com/T34481) | 6.3-rc1  |            |            |         |
| SPI                      | [T36154](https://phabricator.collabora.com/T36154) | 6.1-rc1  |            |            |         |
| I2C                      | [T36154](https://phabricator.collabora.com/T36154) | 6.0-rc1  |            |            |         |
| I2S                      |                                                    | 6.2-rc1  |            |            |         | https://lore.kernel.org/all/20221025124132.399729-1-frattaroli.nicolas@gmail.com/
| CAN                      |                                                    |          |            |            |         |
| SPDIF                    |                                                    |          |            |            |         |
| ADC                      |                                                    |          |            |            |         |
| Thermal ADC              | [T36830](https://phabricator.collabora.com/T36830) |          | n/a        | n/a        | n/a     | EVB1 supported in sre's branch
| Watchdog                 |                                                    |          | n/a        | n/a        | n/a     |
| GPU                      | [T37258](https://phabricator.collabora.com/T37258) |          |            |            |         |
| Multimedia Codecs        |                                                    |          |            |            |         |
|  - CSI Camera support    |                                                    |          |            |            |         |
|  - HDMI Input            |                                                    |          |            |            |         |
|  - AV1                   | [T38796](https://phabricator.collabora.com/T38796) |          |            |            |         |

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://git.kernel.org/pub/scm/linux/kernel/git/sre/linux-misc.git/log/?h=rk3588
