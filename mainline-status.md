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

|                              | SoC            | Rock 5A        | Rock 5B        | Rock 5B+       | EVB1           | Notes |
| ---------------------------- | -------------- | -------------- | -------------- | -------------- | -------------- | ----- |
| PHY naneng combphy           | {+ 6.4-rc1 +}  | {+ 6.8-rc1 +}  | {+ 6.8-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.7-rc1 +}  | DONE  |
| PHY SNPS PCIe3               | {+ 6.6-rc1 +}  | `n/a`          | {+ 6.7-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.7-rc1 +}  | DONE  |
| PHY inno usb2                | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.6-rc1 +}  | DONE  |
| PHY usbdp                    | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | {+ 6.16-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| PHY MIPI CSI DPHY (inno)     | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv2](https://lore.kernel.org/all/20250616-rk3588-csi-dphy-v2-0-7a94f079b712@collabora.com)  |
| PHY MIPI CSI DCPHY (samsung) | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          | Note: only available on certain HW (e.g., the EVB1)     |
| PMIC (rk806)                 | `n/a`          | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.5-rc1 +}  | DONE  |
| I2C Regulator (rk8602)       | `n/a`          | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | `n/a`          | DONE  |
| cpufreq                      | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | {+ 6.16-rc1 +} | {+ 6.11-rc1 +} | DONE  |
| PCIe3                        | {+ 6.6-rc1 +}  | `n/a`          | {+ 6.7-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.7-rc1 +}  | DONE  |
| PCIe2                        | {+ 6.6-rc1 +}  | {+ 6.12-rc1 +} | {+ 6.7-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.7-rc1 +}  | DONE  |
| Ethernet                     | {+ 6.1-rc1 +}  | {+ 6.3-rc1 +}  | `n/a`          | `n/a`          | {+ 6.3-rc1 +}  | DONE  |
| USB 2                        | {+ 6.5-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.6-rc1 +}  | DONE  |
| USB 3 DRD                    | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | {+ 6.10-rc1 +} | {+ 6.16-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| USB 3 Host                   | {+ 6.7-rc1 +}  | {+ 6.8-rc1 +}  | {+ 6.8-rc1 +}  | {+ 6.16-rc1 +} | `n/a`          | DONE  |
| USB-C (fusb302)              | `n/a`          | `n/a`          | sent           | sent           | {+ 6.10-rc1 +} | [PATCHv3](https://lore.kernel.org/linux-rockchip/20250818-rock5bp-for-upstream-v3-1-d13f3cdec86c@kernel.org/) |
| eMMC                         | {+ 6.0-rc1 +}  | {+ 6.3-rc1 +}  | {+ 6.3-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.3-rc1 +}  | DONE  |
| SD Card                      | {+ 6.4-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | {+ 6.16-rc1 +} | `n/a`          | DONE  |
| SDIO                         | {+ 6.5-rc1 +}  | `n/a`          | {+ 6.7-rc1 +}  | {+ 6.16-rc1 +} | `n/a`          | DONE  |
| SATA                         | {+ 6.5-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | {+ 6.6-rc1 +}  | DONE  |
| Timer                        | {+ 6.4-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| OTP                          | {+ 6.5-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| **Display Controller (VOP)** | {+ 6.8-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| - HDMI                       | WIP            | WIP            | WIP            | `n/a`          | WIP            |       |
|  -- HDMI PHY                 | {+ 6.9-rc1 +}  | {+ 6.13-rc1 +} | {+ 6.13-rc1 +} | {+ 6.16-rc1 +} | {+ 6.13-rc1 +} | DONE  |
|  -- HDMI Bridge              | {+ 6.13-rc1 +} | {+ 6.13-rc1 +} | {+ 6.13-rc1 +} | {+ 6.16-rc1 +} | {+ 6.13-rc1 +} | DONE  |
|  -- HDMI Second Port         | {+ 6.15-rc1 +} | {- TODO -}     | {+ 6.15-rc1 +} | {+ 6.16-rc1 +} | {+ 6.15-rc1 +} |       |
|  -- HDMI 4K30 support        | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|  -- HDMI 4K60 support        | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | needs scrambling support |
|  -- HDMI FRL support         | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDMI 8K support          | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDMI Audio               | {+ 6.15-rc1 +} | {- TODO -}     | {+ 6.15-rc1 +} | {+ 6.16-rc1 +} | {- TODO -}     |       |
|  -- HDMI CEC                 | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCH v2](https://lore.kernel.org/lkml/20250710-rk3588-hdmi-cec-v2-0-f5884be34bc1@collabora.com/) |
|  -- HDMI ARC                 | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDCP                     | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| - eDP                        | {+ 6.16-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv8](https://lore.kernel.org/linux-rockchip/20250310104114.2608063-1-damon.ding@rock-chips.com/) |
|  -- eDP PHY                  | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| - DSI                        | {+ 6.16-rc1 +} | {- TODO -}     | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
|  -- DSI PHY                  | {+ 6.15-rc1 +} | {- TODO -}     | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
|  -- DSI Bridge               | {+ 6.14-rc1 +} | {- TODO -}     | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
| - DP1.4 USB-C AltMode        | {- TODO -}     | `n/a`          | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
|  -- DP Bridge                | sent           | `n/a`          | {- TODO -}     | {- TODO -}     | {- TODO -}     | [PATCHv6](https://lore.kernel.org/all/20250728082846.3811429-1-andyshrk@163.com/) |
| M2 E                         | `n/a`          | {+ 6.12-rc1 +} | {+ 6.7-rc1 +}  | `n/a`          | `n/a`          | DONE  |
| M2 M                         | `n/a`          | `n/a`          | {+ 6.7-rc1 +}  | {+ 6.16-rc1 +} | `n/a`          | DONE  |
| Headphone Jack Playback      | `n/a`          | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.8-rc1 +}  | DONE  |
| Headphone Jack Record        | `n/a`          | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.8-rc1 +}  | DONE  |
| Real Time Clock (RTC)        | `n/a`          | `n/a`          | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.3-rc1 +}  | DONE  |
| HW crypto engine             | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv1](https://lore.kernel.org/all/20231107155532.3747113-1-clabbe@baylibre.com/), [working tree from Corentin Labbe](https://github.com/montjoie/linux/commits/rk2-crypto-v1/) |
| Random Number Generator      | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| UART                         | {+ 6.0-rc1 +}  | {+ 6.3-rc1 +}  | {+ 6.3-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.3-rc1 +}  | DONE  |
| GPIO                         | {+ 6.0-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| Pinmux                       | {+ 5.19-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| Interrupts                   | {+ 6.3-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| GICv3 ITS support            | {+ 6.4-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| PWM                          | {+ 6.3-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| PWM FAN                      | `n/a`          | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | `n/a`          | DONE  |
| SPI                          | {+ 6.1-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| I2C                          | {+ 6.0-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| I2S                          | {+ 6.2-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.8-rc1 +}  | DONE  |
| CAN                          | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          | RK356x has an upstream driver |
| SPDIF                        | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| SFC (Flash Controller)       | {+ 6.7-rc1 +}  | {- TODO -}     | {- TODO -}     | {- TODO -}     | `n/a`          |       |
| DFI                          | {+ 6.7-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE (DDR memory utilization for perf) |
| ADC                          | {+ 6.5-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.7-rc1 +}  | DONE  |
| Thermal ADC                  | {+ 6.4-rc1 +}  | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | {+ 6.16-rc1 +} | {+ 6.11-rc1 +} | DONE  |
| Watchdog                     | {+ 6.4-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| GPU                          | {+ 6.10-rc1 +} | {+ 6.13-rc1 +} | {+ 6.10-rc1 +} | {+ 6.16-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| NPU                          | {+ 6.18-rc1 +} | {- TODO -}     | {+ 6.18-rc1 +} | {+ 6.18-rc1 +} | {- TODO -}     | DONE  |
| ISP                          | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| RGA2                         | {+ 6.12-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| RGA3                         | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| HDMI Input                   | {+ 6.15-rc1 +} | `n/a`          | {+ 6.15-rc1 +} | {+ 6.16-rc1 +} | {+ 6.17-rc1 +} |       |
|  - CEC                       | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|  - Audio                     | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - HDCP                      | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| **Video Capture (VICAP)**    | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv10 for RK3568](https://lore.kernel.org/all/20240220-rk3568-vicap-v10-0-62d8a7b209b4@collabora.com/) |
|  - Digital Video Port (DVP)  | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          | Note: is there HW that exposes that? |
|  - MIPI CSI Hosts            | WIP            | `n/a`          | `n/a`          |`n/a`           | `n/a`          | [PATCHv10 for RK3568](https://lore.kernel.org/all/20240220-rk3568-vicap-v10-0-62d8a7b209b4@collabora.com/) provides the driver |
|  - MUX/TOISP                 | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - SCALER                    | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| **Media Encoder**            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VEPU121**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264                   | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                    | {+ 6.12-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | missing multi-core support |
|  - **VEPU580**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.265                   | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264                   | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [WIP by Michael Tretter (Pengutronix)](https://lore.kernel.org/linux-media/Z4e9wNxZjvnytXlL@pengutronix.de/) |
| **Media Decoder**            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU121**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- VC1                     | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- VP8                     | {+ 6.12-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|   -- MPEG-1                  | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- MPEG-2                  | {+ 6.12-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|   -- MPEG-4                  | {+ 6.12-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|   -- H.263                   | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                    | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU381**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- H.264                   | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCH v2](https://lore.kernel.org/linux-rockchip/20250808200340.156393-1-detlev.casanova@collabora.com/) |
|   -- H.265                   | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCH v2](https://lore.kernel.org/linux-rockchip/20250808200340.156393-1-detlev.casanova@collabora.com/) |
|   -- VP9                     | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- AVS2                    | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU720**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                    | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU981**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- AV1                     | {+ 6.7-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|    - AV1 IOMMU               | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv3](https://lore.kernel.org/lkml/20250619131232.69208-1-benjamin.gaignard@collabora.com/) |

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux

RK3588 Improvements (pending)
=============================

 * HDMI PHY FRL support: [PATCHv3](https://lore.kernel.org/linux-rockchip/20250818-phy-hdptx-frl-v3-0-c79997d8bb2b@collabora.com/)
 * PCIe System PM support: [PATCHv3](https://lore.kernel.org/linux-rockchip/1744940759-23823-1-git-send-email-shawn.lin@rock-chips.com/)
 * PCIe slot reset on link down: [PATCHv6](https://lore.kernel.org/linux-pci/20250715-pci-port-reset-v6-0-6f9cce94e7bb@oss.qualcomm.com/)
 * Improved USB-C Orientation handling: [PATCHv2](https://lore.kernel.org/linux-rockchip/20250226103810.3746018-1-heiko@sntech.de/)
 * VOP VP clock reset support: [PATCHv3](https://lore.kernel.org/linux-rockchip/20241108185212.198603-1-detlev.casanova@collabora.com/)
 * Fix Thermal GRF warning: [PATCHv1](https://lore.kernel.org/linux-rockchip/20250818-thermal-rockchip-grf-warning-v1-1-134152c97097@kernel.org/)
 * Limit HDMI infoframes: [PATCHv1](https://lore.kernel.org/linux-rockchip/20250816-drm-limit-infoframes-v1-0-6dc17d5f07e9@oss.qualcomm.com/)

RK3588 Improvements (merged)
============================

 * FUSB302 race condition fix (6.17-rc1): [PATCHv1](https://lore.kernel.org/all/20250704-fusb302-race-condition-fix-v1-1-239012c0e27a@kernel.org/)
 * PCIe ASPM L0S capability (6.16-rc1): [PATCHv4](https://lore.kernel.org/linux-rockchip/1744850111-236269-1-git-send-email-shawn.lin@rock-chips.com/)
 * AV1 4K support (6.17-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/20250217-b4-hantro-av1-clock-rate-v2-1-e179fad52641@collabora.com/)
 * HDMI DDC drive strength (6.17-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/20250522020537.1884771-1-andyshrk@163.com/)
 * HDMI YUV420 support infrastructure (6.17-rc1): [PATCHv5](https://lore.kernel.org/dri-devel/20250527-hdmi-conn-yuv-v5-0-74c9c4a8ac0c@collabora.com/)
 * HDMI PHY color depth management (6.16-rc1): [PATCHv6](https://lore.kernel.org/linux-rockchip/20250318-phy-sam-hdptx-bpc-v6-0-8cb1678e7663@collabora.com/)
 * GPU Power Domain fix (6.16-rc1): [PATCHv6](https://lore.kernel.org/linux-rockchip/20250220-rk3588-gpu-pwr-domain-regulator-v6-0-a4f9c24e5b81@kernel.org/)
 * eMMC command queuing engine support (6.11-rc1): [PATCHv1 CQE](https://lore.kernel.org/all/20240530215547.2192457-1-heiko@sntech.de/)
 * PCIe endpoint mode support (6.11-rc1): [PATCHv5](https://lore.kernel.org/all/20240607-rockchip-pcie-ep-v1-v5-0-0a042d6b0049@kernel.org/)
 * Improved linked clock gate support (6.14-rc1): [PATCHv12](https://lore.kernel.org/linux-rockchip/20241211165957.94922-1-sebastian.reichel@collabora.com/)
