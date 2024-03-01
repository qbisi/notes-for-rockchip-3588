RK3588 Mainline Kernel support
==============================

This table lists the hardware features available by RK3588/RK3588S. The SoC
(System on a Chip) column is about kernel driver support. Then there is one
column for each board used by Collabora's engineers. Those are about the
current status of the board DT (device tree). Note, that we are mainly
focusing on the Rock 5B.

If a version is provided, that's the first kernel version supporting this
feature. "n/a" means "not available/applicable". For example the Rock 5A
is based on RK3588S and that does not have HDMI-RX. Other than that there
is "sent" used when things have been sent to the upstream mailinglists for
review and "ready" for things available from our integration branch. Those
are close to upstream quality and either close to being send upstream for
review or blocked by a missing feature.

|                          | Issue                                                                                   | SoC             | Rock Pi 5A    | Rock Pi 5B    | EVB1          | Notes |
| ------------------------ | --------------------------------------------------------------------------------------- | --------------- | ------------- | ------------- | ------------- | ----- |
| PHY naneng combphy       |                                                                                         | {+ 6.4-rc1 +}   | {+ 6.8-rc1 +} | {+ 6.8-rc1 +} | {+ 6.7-rc1 +} | DONE  |
| PHY SNPS PCIe3           |                                                                                         | {+ 6.6-rc1 +}   | `n/a`         | {+ 6.7-rc1 +} | {+ 6.7-rc1 +} | DONE  |
| PHY inno usb2            |                                                                                         | {+ 6.6-rc1 +}   | {+ 6.6-rc1 +} | {+ 6.6-rc1 +} | {+ 6.6-rc1 +} | DONE  |
| PHY usbdp                | [#3](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/3)   | sent            | sent          | sent          | sent          | [PATCHv3](https://lore.kernel.org/all/20240216170514.75200-1-sebastian.reichel@collabora.com/) |
| PMIC (rk806)             |                                                                                         | `n/a`           | {+ 6.6-rc1 +} | {+ 6.5-rc1 +} | {+ 6.5-rc1 +} | DONE  |
| I2C Regulator (rk8602)   |                                                                                         | `n/a`           | {+ 6.6-rc1 +} | {+ 6.4-rc1 +} | `n/a`         | DONE  |
| USB-PD Controller        | [#8](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/8)   | `n/a`           | `n/a`         | ready         | ready         |       |
| cpufreq                  | [#7](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/7)   | WIP             | WIP           | WIP           | WIP           | [PATCHv2 from Alexey Charkov](https://lore.kernel.org/linux-rockchip/20240130-rk-dts-additions-v2-0-c6222c4c78df@gmail.com/) |
| PCIe3                    |                                                                                         | {+ 6.6-rc1 +}   | `n/a`         | {+ 6.7-rc1 +} | {+ 6.7-rc1 +} | DONE  |
| PCIe2                    |                                                                                         | {+ 6.6-rc1 +}   | {- TODO -}    | {+ 6.7-rc1 +} | {+ 6.7-rc1 +} | DONE  |
| Ethernet                 |                                                                                         | {+ 6.1-rc1 +}   | {+ 6.3-rc1 +} | `n/a`         | {+ 6.3-rc1 +} | DONE  |
| USB 2                    |                                                                                         | {+ 6.5-rc1 +}   | {+ 6.6-rc1 +} | {+ 6.6-rc1 +} | {+ 6.6-rc1 +} | DONE  |
| USB 3 DRD                | [#3](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/3)   | sent            | sent          | sent          | sent          | [PATCHv3](https://lore.kernel.org/all/20240216170514.75200-1-sebastian.reichel@collabora.com/) |
| USB 3 Host               |                                                                                         | {+ 6.7-rc1 +}   | {+ 6.8-rc1 +} | {+ 6.8-rc1 +} | `n/a`         | DONE  |
| USB-C                    | [#8](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/8)   | `n/a`           | `n/a`         | ready         | sent          |       |
| eMMC                     |                                                                                         | {+ 6.0-rc1 +}   | {+ 6.3-rc1 +} | {+ 6.3-rc1 +} | {+ 6.3-rc1 +} | DONE  |
| SD Card                  |                                                                                         | {+ 6.4-rc1 +}   | {+ 6.6-rc1 +} | {+ 6.5-rc1 +} | `n/a`         | DONE  |
| SDIO                     |                                                                                         | {+ 6.5-rc1 +}   | `n/a`         | {+ 6.7-rc1 +} | `n/a`         | DONE  |
| SATA                     |                                                                                         | {+ 6.5-rc1 +}   | `n/a`         | `n/a`         | {+ 6.6-rc1 +} | DONE  |
| Timer                    |                                                                                         | {+ 6.4-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| OTP                      |                                                                                         | {+ 6.5-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| **Display Controller (VOP)** |                                                                                     | {+ 6.8-rc1 +}   | {- TODO -}    | WIP           | WIP           |       |
| - HDMI                   | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | WIP             | {- TODO -}    | WIP           | WIP           |       |
|  -- HDMI PHY             | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | {+ 6.9-rc1 +}   | {- TODO -}    | ready         | ready         | [PATCHv4](https://lore.kernel.org/all/20240214-phy-hdptx-v4-0-e7974f46c1a7@collabora.com/) |
|  -- HDMI Bridge          | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | WIP             | {- TODO -}    | WIP           | WIP           |       |
|  -- HDMI Audio           |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|  -- HDCP                 |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
| - DSI                    |                                                                                         | {- TODO -}      | {- TODO -}    | {- TODO -}    | {- TODO -}    |       |
| - DP1.4 USB-C AltMode    |                                                                                         | {- TODO -}      | `n/a`         | {- TODO -}    | {- TODO -}    |       |
| M2 E                     |                                                                                         | `n/a`           | {- TODO -}    | partial       | `n/a`         | requires SDIO, PCIe2, I2S, UART, I2C, USB3; Rock 5B has partial support in v6.7-rc1 |
| M2 M                     |                                                                                         | `n/a`           | `n/a`         | {+ 6.7-rc1 +} | `n/a`         | DONE  |
| Headphone Jack Playback  |                                                                                         | `n/a`           | {+ 6.6-rc1 +} | {+ 6.4-rc1 +} | {+ 6.8-rc1 +} | DONE  |
| Headphone Jack Record    |                                                                                         | `n/a`           | {+ 6.6-rc1 +} | {+ 6.4-rc1 +} | {+ 6.8-rc1 +} | DONE  |
| Real Time Clock (RTC)    |                                                                                         | `n/a`           | `n/a`         | {+ 6.4-rc1 +} | {+ 6.3-rc1 +} | DONE  |
| HW crypto engine         |                                                                                         | sent            | `n/a`         | `n/a`         | `n/a`         | [PATCHv1](https://lore.kernel.org/all/20231107155532.3747113-1-clabbe@baylibre.com/) |
| Random Number Generator  |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
| UART                     |                                                                                         | {+ 6.0-rc1 +}   | {+ 6.3-rc1 +} | {+ 6.3-rc1 +} | {+ 6.3-rc1 +} | DONE  |
| GPIO                     |                                                                                         | {+ 6.0-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| Pinmux                   |                                                                                         | {+ 5.19-rc1 +}  | `n/a`         | `n/a`         | `n/a`         | DONE  |
| Interrupts               |                                                                                         | {+ 6.3-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| GICv3 ITS support        |                                                                                         | {+ 6.4-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| PWM                      |                                                                                         | {+ 6.3-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| PWM FAN                  |                                                                                         | `n/a`           | {+ 6.6-rc1 +} | {+ 6.4-rc1 +} | `n/a`         | DONE  |
| SPI                      |                                                                                         | {+ 6.1-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| I2C                      |                                                                                         | {+ 6.0-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| I2S                      |                                                                                         | {+ 6.2-rc1 +}   | {+ 6.6-rc1 +} | {+ 6.4-rc1 +} | {+ 6.8-rc1 +} | DONE  |
| CAN                      |                                                                                         | ?               | `n/a`         | `n/a`         | `n/a`         | [WIP branch from Pengutronix](https://git.kernel.org/pub/scm/linux/kernel/git/mkl/linux-can-next.git/log/?h=rockchip-canfd) |
| SPDIF                    |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
| SFC (Flash Controller)   |                                                                                         | {+ 6.7-rc1 +}   | {- TODO -}    | {- TODO -}    | `n/a`         |       |
| OTP Memory               |                                                                                         | {+ 6.5-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| DFI                      |                                                                                         | {+ 6.7-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE (DDR memory utilization for perf) |
| ADC                      |                                                                                         | {+ 6.5-rc1 +}   | {+ 6.6-rc1 +} | {+ 6.5-rc1 +} | {+ 6.7-rc1 +} | DONE  |
| Thermal ADC              |                                                                                         | {+ 6.4-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | pending patch to enable it at SoC level |
| Watchdog                 |                                                                                         | {+ 6.4-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |
| GPU                      |                                                                                         | {+ 6.9-rc1 +}   | {- TODO -}    | ready         | ready         | [PATCHv6](https://lore.kernel.org/all/20240229162230.2634044-1-boris.brezillon@collabora.com/), [Blog Post](https://www.collabora.com/news-and-blog/news-and-events/pancsf-a-new-drm-driver-for-mali-csf-based-gpus.html) |
| NPU                      |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         | [reverse-engineering project](http://jas-hacks.blogspot.com/2024/02/rk3588-reverse-engineering-rknn.html), [downstream kernel driver](https://github.com/friendlyarm/kernel-rockchip/commits/nanopi6-v6.1.y/drivers/rknpu) |
| ISP                      |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
| HDMI Input               | [#4](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/4)   | sent            | `n/a`         | sent          | {- TODO -}    | [PATCHv1](https://lore.kernel.org/linux-rockchip/20240216094922.257674-1-shreeya.patel@collabora.com/) |
|  - CEC                   | [#4](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/4)   | sent            | `n/a`         | `n/a`         | `n/a`         | [PATCHv1](https://lore.kernel.org/linux-rockchip/20240216094922.257674-1-shreeya.patel@collabora.com/) |
|  - Audio                 |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|  - HDCP                  |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
| **Video Capture (VICAP)** |                                                                                        | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         | [PATCHv1 for RK3568](https://lore.kernel.org/all/20240220-v6-8-topic-rk3568-vicap-v1-0-2680a1fa640b@wolfvision.net/) |
|  - MIPI CSI              |                                                                                         | {- TODO -}      | {- TODO -}    | {- TODO -}    | {- TODO -}    |       |
| **Media Encoder**        |                                                                                         | `n/a`           | `n/a`         | `n/a`         | `n/a`         |       |
|  - **VEPU121**           |                                                                                         | `n/a`           | `n/a`         | `n/a`         | `n/a`         |       |
|   -- H.264               |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|   -- JPEG                |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|  - **VEPU580**           |                                                                                         | `n/a`           | `n/a`         | `n/a`         | `n/a`         |       |
|   -- H.265               |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|   -- H.264               |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
| **Media Decoder**        |                                                                                         | `n/a`           | `n/a`         | `n/a`         | `n/a`         |       |
|  - **VDPU121**           |                                                                                         | `n/a`           | `n/a`         | `n/a`         | `n/a`         |       |
|   -- VC1                 |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|   -- VP8                 |                                                                                         | WIP             | `n/a`         | `n/a`         | `n/a`         | [PATCHv3](https://lore.kernel.org/all/20231231151112.3994194-1-liujianfeng1994@gmail.com/) |
|   -- MPEG-1              |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|   -- MPEG-2              |                                                                                         | WIP             | `n/a`         | `n/a`         | `n/a`         | [PATCHv3](https://lore.kernel.org/all/20231231151112.3994194-1-liujianfeng1994@gmail.com/) |
|   -- MPEG-4              |                                                                                         | WIP             | `n/a`         | `n/a`         | `n/a`         | [PATCHv3](https://lore.kernel.org/all/20231231151112.3994194-1-liujianfeng1994@gmail.com/) |
|   -- H.263               |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|   -- JPEG                |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|  - **VDPU381**           |                                                                                         | `n/a`           | `n/a`         | `n/a`         | `n/a`         |       |
|   -- H.264               |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|   -- H.265               |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|   -- VP9                 |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|   -- AVS2                |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|  - **VDPU720**           |                                                                                         | `n/a`           | `n/a`         | `n/a`         | `n/a`         |       |
|   -- JPEG                |                                                                                         | {- TODO -}      | `n/a`         | `n/a`         | `n/a`         |       |
|  - **VDPU981**           |                                                                                         | `n/a`           | `n/a`         | `n/a`         | `n/a`         |       |
|   -- AV1                 |                                                                                         | {+ 6.7-rc1 +}   | `n/a`         | `n/a`         | `n/a`         | DONE  |

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux

RK3588 Improvements
===================

 * Improved linked clock gate support: [PATCHv7](https://lore.kernel.org/all/20231213185114.47565-1-sebastian.reichel@collabora.com/)
 * eMMC command queuing engine support: [PATCHv5 CQE](https://lore.kernel.org/all/20231231144619.758290-1-serghox@gmail.com/)
