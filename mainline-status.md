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

|                          | Issue                                                                                   | SoC             | Rock Pi 5A     | Rock Pi 5B     | EVB1           | Notes |
| ------------------------ | --------------------------------------------------------------------------------------- | --------------- | -------------- | -------------- | -------------- | ----- |
| PHY naneng combphy       |                                                                                         | {+ 6.4-rc1 +}   | {+ 6.8-rc1 +}  | {+ 6.8-rc1 +}  | {+ 6.7-rc1 +}  | DONE  |
| PHY SNPS PCIe3           |                                                                                         | {+ 6.6-rc1 +}   | `n/a`          | {+ 6.7-rc1 +}  | {+ 6.7-rc1 +}  | DONE  |
| PHY inno usb2            |                                                                                         | {+ 6.6-rc1 +}   | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | DONE  |
| PHY usbdp                | [#3](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/3)   | {+ 6.10-rc1 +}  | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| PMIC (rk806)             |                                                                                         | `n/a`           | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | {+ 6.5-rc1 +}  | DONE  |
| I2C Regulator (rk8602)   |                                                                                         | `n/a`           | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | `n/a`          | DONE  |
| cpufreq                  | [#7](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/7)   | sent            | sent           | sent           | sent           | [PATCHv4 from Alexey Charkov](https://lore.kernel.org/linux-rockchip/20240506-rk-dts-additions-v4-0-271023ddfd40@gmail.com/) |
| PCIe3                    |                                                                                         | {+ 6.6-rc1 +}   | `n/a`          | {+ 6.7-rc1 +}  | {+ 6.7-rc1 +}  | DONE  |
| PCIe2                    |                                                                                         | {+ 6.6-rc1 +}   | {- TODO -}     | {+ 6.7-rc1 +}  | {+ 6.7-rc1 +}  | DONE  |
| Ethernet                 |                                                                                         | {+ 6.1-rc1 +}   | {+ 6.3-rc1 +}  | `n/a`          | {+ 6.3-rc1 +}  | DONE  |
| USB 2                    |                                                                                         | {+ 6.5-rc1 +}   | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | DONE  |
| USB 3 DRD                | [#3](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/3)   | {+ 6.10-rc1 +}  | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| USB 3 Host               |                                                                                         | {+ 6.7-rc1 +}   | {+ 6.8-rc1 +}  | {+ 6.8-rc1 +}  | `n/a`          | DONE  |
| USB-C (fusb302)          | [#8](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/8)   | `n/a`           | `n/a`          | WIP            | {+ 6.10-rc1 +} |       |
| eMMC                     |                                                                                         | {+ 6.0-rc1 +}   | {+ 6.3-rc1 +}  | {+ 6.3-rc1 +}  | {+ 6.3-rc1 +}  | DONE  |
| SD Card                  |                                                                                         | {+ 6.4-rc1 +}   | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | `n/a`          | DONE  |
| SDIO                     |                                                                                         | {+ 6.5-rc1 +}   | `n/a`          | {+ 6.7-rc1 +}  | `n/a`          | DONE  |
| SATA                     |                                                                                         | {+ 6.5-rc1 +}   | `n/a`          | `n/a`          | {+ 6.6-rc1 +}  | DONE  |
| Timer                    |                                                                                         | {+ 6.4-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| OTP                      |                                                                                         | {+ 6.5-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| **Display Controller (VOP)** |                                                                                     | {+ 6.8-rc1 +}   | {- TODO -}     | WIP            | WIP            |       |
| - HDMI                   | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | WIP             | {- TODO -}     | WIP            | WIP            |       |
|  -- HDMI PHY             | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | {+ 6.9-rc1 +}   | {- TODO -}     | ready          | ready          |       |
|  -- HDMI Bridge          | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | sent            | {- TODO -}     | WIP            | WIP            | [PATCHv1](https://lore.kernel.org/linux-rockchip/a5jlj5hncv2p7lxk6pbgynkqfovlg3lzz2muzrbrkd73afiopu@n5tmd4zfyeik/) |
|  -- HDMI Audio           |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDCP                 |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| - DSI                    |                                                                                         | WIP             | {- TODO -}     | {- TODO -}     | {- TODO -}     | WIP by Heiko Stübner |
|  -- DSI  PHY             |                                                                                         | sent            | {- TODO -}     | {- TODO -}     | {- TODO -}     | [DC-PHY driver PATCHv1](https://lore.kernel.org/linux-phy/20240506124836.3621528-1-heiko@sntech.de/), [DC-PHY syscon PATCHv1](https://lore.kernel.org/linux-rockchip/f44c76ac-3dc1-45d6-b435-e5b77b708d6e@cherry.de/) |
|  -- DSI  Bridge          |                                                                                         | WIP             | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
| - DP1.4 USB-C AltMode    |                                                                                         | {- TODO -}      | `n/a`          | {- TODO -}     | {- TODO -}     |       |
| M2 E                     |                                                                                         | `n/a`           | {- TODO -}     | partial        | `n/a`          | requires SDIO, PCIe2, I2S, UART, I2C, USB3; Rock 5B has partial support in v6.7-rc1 |
| M2 M                     |                                                                                         | `n/a`           | `n/a`          | {+ 6.7-rc1 +}  | `n/a`          | DONE  |
| Headphone Jack Playback  |                                                                                         | `n/a`           | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.8-rc1 +}  | DONE  |
| Headphone Jack Record    |                                                                                         | `n/a`           | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.8-rc1 +}  | DONE  |
| Real Time Clock (RTC)    |                                                                                         | `n/a`           | `n/a`          | {+ 6.4-rc1 +}  | {+ 6.3-rc1 +}  | DONE  |
| HW crypto engine         |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv1](https://lore.kernel.org/all/20231107155532.3747113-1-clabbe@baylibre.com/), [working tree from Corentin Labbe](https://github.com/montjoie/linux/commits/rk2-crypto-v1/) |
| Random Number Generator  |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| UART                     |                                                                                         | {+ 6.0-rc1 +}   | {+ 6.3-rc1 +}  | {+ 6.3-rc1 +}  | {+ 6.3-rc1 +}  | DONE  |
| GPIO                     |                                                                                         | {+ 6.0-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| Pinmux                   |                                                                                         | {+ 5.19-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | DONE  |
| Interrupts               |                                                                                         | {+ 6.3-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| GICv3 ITS support        |                                                                                         | {+ 6.4-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| PWM                      |                                                                                         | {+ 6.3-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| PWM FAN                  |                                                                                         | `n/a`           | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | `n/a`          | DONE  |
| SPI                      |                                                                                         | {+ 6.1-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| I2C                      |                                                                                         | {+ 6.0-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| I2S                      |                                                                                         | {+ 6.2-rc1 +}   | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.8-rc1 +}  | DONE  |
| CAN                      |                                                                                         | ?               | `n/a`          | `n/a`          | `n/a`          | [WIP branch from Pengutronix](https://git.kernel.org/pub/scm/linux/kernel/git/mkl/linux-can-next.git/log/?h=rockchip-canfd) |
| SPDIF                    |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| SFC (Flash Controller)   |                                                                                         | {+ 6.7-rc1 +}   | {- TODO -}     | {- TODO -}     | `n/a`          |       |
| OTP Memory               |                                                                                         | {+ 6.5-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| DFI                      |                                                                                         | {+ 6.7-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE (DDR memory utilization for perf) |
| ADC                      |                                                                                         | {+ 6.5-rc1 +}   | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | {+ 6.7-rc1 +}  | DONE  |
| Thermal ADC              |                                                                                         | {+ 6.4-rc1 +}   | sent           | sent           | sent           | [PATCHv4 from Alexey Charkov](https://lore.kernel.org/linux-rockchip/20240506-rk-dts-additions-v4-0-271023ddfd40@gmail.com/) |
| Watchdog                 |                                                                                         | {+ 6.4-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| GPU                      |                                                                                         | {+ 6.10-rc1 +}  | {- TODO -}     | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | [Blog Post](https://www.collabora.com/news-and-blog/news-and-events/release-the-panthor.html)
| NPU                      |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv1](https://lore.kernel.org/all/20240612-6-10-rocket-v1-0-060e48eea250@tomeuvizoso.net/) |
| ISP                      |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| RGA2                     |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv1](https://lore.kernel.org/all/20240322052915.3507937-1-liujianfeng1994@gmail.com/) |
| RGA3                     |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| HDMI Input               | [#4](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/4)   | sent            | `n/a`          | sent           | {- TODO -}     | [PATCHv3](https://lore.kernel.org/all/20240327225057.672304-1-shreeya.patel@collabora.com/) |
|  - CEC                   | [#4](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/4)   | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv3](https://lore.kernel.org/all/20240327225057.672304-1-shreeya.patel@collabora.com/) |
|  - Audio                 |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  - HDCP                  |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| **Video Capture (VICAP)** |                                                                                        | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          | [PATCHv1 for RK3568](https://lore.kernel.org/all/20240220-v6-8-topic-rk3568-vicap-v1-0-2680a1fa640b@wolfvision.net/) |
|  - MIPI CSI              |                                                                                         | {- TODO -}      | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
| **Media Encoder**        |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VEPU121**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264               |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv5](https://lore.kernel.org/linux-rockchip/20240612173213.42827-1-sebastian.reichel@collabora.com/) |
|  - **VEPU580**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.265               |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264               |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| **Media Decoder**        |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU121**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- VC1                 |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- VP8                 |                                                                                         | WIP             | `n/a`          | `n/a`          | `n/a`          | [PATCHv5](https://lore.kernel.org/linux-rockchip/20240612173213.42827-1-sebastian.reichel@collabora.com/) |
|   -- MPEG-1              |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- MPEG-2              |                                                                                         | WIP             | `n/a`          | `n/a`          | `n/a`          | [PATCHv5](https://lore.kernel.org/linux-rockchip/20240612173213.42827-1-sebastian.reichel@collabora.com/) |
|   -- MPEG-4              |                                                                                         | WIP             | `n/a`          | `n/a`          | `n/a`          | [PATCHv5](https://lore.kernel.org/linux-rockchip/20240612173213.42827-1-sebastian.reichel@collabora.com/) |
|   -- H.263               |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU381**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264               |                                                                                         | WIP             | `n/a`          | `n/a`          | `n/a`          | WIP by Detlev Casanova |
|   -- H.265               |                                                                                         | WIP             | `n/a`          | `n/a`          | `n/a`          | Work starting soon(tm) |
|   -- VP9                 |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- AVS2                |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU720**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU981**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- AV1                 |                                                                                         | {+ 6.7-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux

RK3588 Improvements
===================

 * PCIe endpoint mode support: [PATCHv3](https://lore.kernel.org/linux-rockchip/20240508-rockchip-pcie-ep-v1-v3-0-1748e202b084@kernel.org/)
 * Improved linked clock gate support: [PATCHv9](https://lore.kernel.org/all/20240325193609.237182-1-sebastian.reichel@collabora.com/)
 * eMMC command queuing engine support: [PATCHv1 CQE](https://lore.kernel.org/all/20240530215547.2192457-1-heiko@sntech.de/)
