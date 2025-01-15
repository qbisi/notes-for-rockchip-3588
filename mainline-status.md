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
| cpufreq                  | [#7](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/7)   | {+ 6.11-rc1 +}  | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | DONE  |
| PCIe3                    |                                                                                         | {+ 6.6-rc1 +}   | `n/a`          | {+ 6.7-rc1 +}  | {+ 6.7-rc1 +}  | DONE  |
| PCIe2                    |                                                                                         | {+ 6.6-rc1 +}   | {- TODO -}     | {+ 6.7-rc1 +}  | {+ 6.7-rc1 +}  | DONE  |
| Ethernet                 |                                                                                         | {+ 6.1-rc1 +}   | {+ 6.3-rc1 +}  | `n/a`          | {+ 6.3-rc1 +}  | DONE  |
| USB 2                    |                                                                                         | {+ 6.5-rc1 +}   | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | DONE  |
| USB 3 DRD                | [#3](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/3)   | {+ 6.10-rc1 +}  | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| USB 3 Host               |                                                                                         | {+ 6.7-rc1 +}   | {+ 6.8-rc1 +}  | {+ 6.8-rc1 +}  | `n/a`          | DONE  |
| USB-C (fusb302)          | [#8](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/8)   | `n/a`           | `n/a`          | sent           | {+ 6.10-rc1 +} | [PATCHv1](https://lore.kernel.org/linux-rockchip/20241210163615.120594-1-sebastian.reichel@collabora.com/) |
| eMMC                     |                                                                                         | {+ 6.0-rc1 +}   | {+ 6.3-rc1 +}  | {+ 6.3-rc1 +}  | {+ 6.3-rc1 +}  | DONE  |
| SD Card                  |                                                                                         | {+ 6.4-rc1 +}   | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | `n/a`          | DONE  |
| SDIO                     |                                                                                         | {+ 6.5-rc1 +}   | `n/a`          | {+ 6.7-rc1 +}  | `n/a`          | DONE  |
| SATA                     |                                                                                         | {+ 6.5-rc1 +}   | `n/a`          | `n/a`          | {+ 6.6-rc1 +}  | DONE  |
| Timer                    |                                                                                         | {+ 6.4-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| OTP                      |                                                                                         | {+ 6.5-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| **Display Controller (VOP)** |                                                                                     | {+ 6.8-rc1 +}   | `n/a`          | `n/a`          | `n/a`          |       |
| - HDMI                   | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | WIP             | WIP            | WIP            | WIP            |       |
|  -- HDMI PHY             | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | {+ 6.9-rc1 +}   | {+ 6.13-rc1 +} | {+ 6.13-rc1 +} | {+ 6.13-rc1 +} | DONE  |
|  -- HDMI Bridge          | [#5](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/5)   | {+ 6.13-rc1 +}  | {+ 6.13-rc1 +} | {+ 6.13-rc1 +} | {+ 6.13-rc1 +} | DONE  |
|  -- HDMI 4K support      |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv2](https://lore.kernel.org/all/20241211-vop2-hdmi0-disp-modes-v2-0-471cf5001e45@collabora.com/) |
|  -- HDMI FRL support     |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDMI 8K support      |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDMI Second Port     |                                                                                         | sent            | {- TODO -}     | sent           | {- TODO -}     | [PATCHv2](https://lore.kernel.org/linux-rockchip/20241211-rk3588-hdmi1-v2-0-02cdca22ff68@collabora.com/) |
|  -- HDMI CEC             |                                                                                         | WIP             | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDMI Audio           |                                                                                         | WIP             | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDMI ARC             |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDCP                 |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| - eDP                    |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv9](https://lore.kernel.org/linux-rockchip/20250109032725.1102465-1-damon.ding@rock-chips.com/) |
|  -- eDP PHY              |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv1](https://lore.kernel.org/linux-rockchip/20250112090714.1564158-1-damon.ding@rock-chips.com/) |
| - DSI                    |                                                                                         | sent            | {- TODO -}     | {- TODO -}     | {- TODO -}     | WIP by Heiko Stübner |
|  -- DSI PHY              |                                                                                         | sent            | {- TODO -}     | {- TODO -}     | {- TODO -}     | [DC-PHY driver PATCHv5](https://lore.kernel.org/linux-rockchip/20241203164934.1500616-1-heiko@sntech.de/) |
|  -- DSI Bridge           |                                                                                         | {+ 6.14-rc1 +}  | {- TODO -}     | {- TODO -}     | {- TODO -}     | [Bridge driver PATCHv4](https://lore.kernel.org/linux-rockchip/20241209231021.2180582-1-heiko@sntech.de/) |
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
| CAN                      |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          | [PATCHv5 for RK3568](https://lore.kernel.org/linux-rockchip/20240904-rockchip-canfd-v5-0-8ae22bcb27cc@pengutronix.de/) |
| SPDIF                    |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| SFC (Flash Controller)   |                                                                                         | {+ 6.7-rc1 +}   | {- TODO -}     | {- TODO -}     | `n/a`          |       |
| OTP Memory               |                                                                                         | {+ 6.5-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| DFI                      |                                                                                         | {+ 6.7-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE (DDR memory utilization for perf) |
| ADC                      |                                                                                         | {+ 6.5-rc1 +}   | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | {+ 6.7-rc1 +}  | DONE  |
| Thermal ADC              |                                                                                         | {+ 6.4-rc1 +}   | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | DONE  |
| Watchdog                 |                                                                                         | {+ 6.4-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |
| GPU                      |                                                                                         | {+ 6.10-rc1 +}  | {+ 6.13-rc1 +} | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| NPU                      |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv1](https://lore.kernel.org/all/20240612-6-10-rocket-v1-0-060e48eea250@tomeuvizoso.net/) |
| ISP                      |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| RGA2                     |                                                                                         | {+ 6.12-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | [PATCHv3](https://lore.kernel.org/linux-rockchip/20240831182424.758816-1-liujianfeng1994@gmail.com/) |
| RGA3                     |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| HDMI Input               | [#4](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/4)   | sent            | `n/a`          | sent           | {- TODO -}     | [PATCHv5](https://lore.kernel.org/linux-rockchip/20241210193904.883225-1-shreeya.patel@collabora.com/) |
|  - CEC                   | [#4](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux/-/issues/4)   | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv5](https://lore.kernel.org/linux-rockchip/20241210193904.883225-1-shreeya.patel@collabora.com/) |
|  - Audio                 |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  - HDCP                  |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| **Video Capture (VICAP)** |                                                                                        | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          | [PATCHv2 for RK3568](https://lore.kernel.org/linux-rockchip/20241217-v6-8-topic-rk3568-vicap-v2-0-b1d488fcc0d3@wolfvision.net/) |
|  - MIPI CSI              |                                                                                         | {- TODO -}      | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
| **Media Encoder**        |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VEPU121**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264               |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                |                                                                                         | {+ 6.12-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | [PATCHv7](https://lore.kernel.org/all/20240618183816.77597-1-sebastian.reichel@collabora.com/) |
|  - **VEPU580**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          | [WIP by Michael Tretter (Pengutronix)](https://lore.kernel.org/linux-media/Z4e9wNxZjvnytXlL@pengutronix.de/) |
|   -- H.265               |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264               |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
| **Media Decoder**        |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU121**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- VC1                 |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- VP8                 |                                                                                         | {+ 6.12-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | [PATCHv7](https://lore.kernel.org/all/20240618183816.77597-1-sebastian.reichel@collabora.com/) |
|   -- MPEG-1              |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- MPEG-2              |                                                                                         | {+ 6.12-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | [PATCHv7](https://lore.kernel.org/all/20240618183816.77597-1-sebastian.reichel@collabora.com/) |
|   -- MPEG-4              |                                                                                         | {+ 6.12-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | [PATCHv7](https://lore.kernel.org/all/20240618183816.77597-1-sebastian.reichel@collabora.com/) |
|   -- H.263               |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU381**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264               |                                                                                         | sent            | `n/a`          | `n/a`          | `n/a`          | [PATCHv2](https://lore.kernel.org/all/20240619150029.59730-1-detlev.casanova@collabora.com/) |
|   -- H.265               |                                                                                         | WIP             | `n/a`          | `n/a`          | `n/a`          |       |
|   -- VP9                 |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|   -- AVS2                |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU720**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                |                                                                                         | {- TODO -}      | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU981**           |                                                                                         | `n/a`           | `n/a`          | `n/a`          | `n/a`          |       |
|   -- AV1                 |                                                                                         | {+ 6.7-rc1 +}   | `n/a`          | `n/a`          | `n/a`          | DONE  |

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux

RK3588 Improvements (pending)
=============================

 * HDMI PHY color depth management: [PATCHv2](https://lore.kernel.org/linux-rockchip/20241212-phy-sam-hdptx-bpc-v2-0-57e672c7c7c4@collabora.com/)
 * Improved linked clock gate support: [PATCHv12](https://lore.kernel.org/linux-rockchip/20241211165957.94922-1-sebastian.reichel@collabora.com/)
 * GPU Power Domain fix: [PATCHv5](https://lore.kernel.org/linux-rockchip/20241211143044.9550-1-sebastian.reichel@collabora.com/)

RK3588 Improvements (merged)
============================

 * eMMC command queuing engine support (6.11-rc1): [PATCHv1 CQE](https://lore.kernel.org/all/20240530215547.2192457-1-heiko@sntech.de/)
 * PCIe endpoint mode support (6.11-rc1): [PATCHv5](https://lore.kernel.org/all/20240607-rockchip-pcie-ep-v1-v5-0-0a042d6b0049@kernel.org/)
