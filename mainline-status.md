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
| PHY MIPI CSI DPHY (inno)     | {+ 6.18-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
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
| USB-C (fusb302)              | `n/a`          | `n/a`          | {+ 6.18-rc1 +} | {+ 6.18-rc1 +} | {+ 6.10-rc1 +} | DONE  |
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
|  -- HDMI 4K60 support        | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv3](https://lore.kernel.org/linux-rockchip/20260119-dw-hdmi-qp-scramb-v3-0-bd8611730fc1@collabora.com/) |
|  -- HDMI FRL support         | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | Fixed Rate Link is needed for resolutions above 4K60 (HDMI 2.1); PHY side has been merged for 7.0-rc1 |
|  -- HDMI 8K support          | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDMI Audio               | {+ 6.15-rc1 +} | {- TODO -}     | {+ 6.15-rc1 +} | {+ 6.16-rc1 +} | {- TODO -}     |       |
|  -- HDMI CEC                 | {+ 6.19-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|  -- HDMI ARC                 | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  -- HDCP                     | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| - eDP                        | {+ 6.16-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|  -- eDP PHY                  | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| - DSI                        | {+ 6.16-rc1 +} | `n/a`          | `n/a`          | `n/a`          | {- TODO -}     |       |
|  -- DSI PHY                  | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | {- TODO -}     |       |
|  -- DSI Bridge               | {+ 6.14-rc1 +} | `n/a`          | `n/a`          | `n/a`          | {- TODO -}     |       |
| - DP1.4 USB-C AltMode        | {- TODO -}     | `n/a`          | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
|  -- DP Bridge                | {+ 6.18-rc1 +} | `n/a`          | {- TODO -}     | {- TODO -}     | {- TODO -}     | DONE, some DT binding updates required for proper USB-C AltMode support |
|    -- Audio                  | WIP            | `n/a`          | {- TODO -}     | {- TODO -}     | {- TODO -}     |       |
| M2 E                         | `n/a`          | {+ 6.12-rc1 +} | {+ 6.7-rc1 +}  | `n/a`          | `n/a`          | DONE  |
| M2 M                         | `n/a`          | `n/a`          | {+ 6.7-rc1 +}  | {+ 6.16-rc1 +} | `n/a`          | DONE  |
| Headphone Jack Playback      | `n/a`          | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.8-rc1 +}  | DONE  |
| Headphone Jack Record        | `n/a`          | {+ 6.6-rc1 +}  | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.8-rc1 +}  | DONE  |
| Real Time Clock (RTC)        | `n/a`          | `n/a`          | {+ 6.4-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.3-rc1 +}  | DONE  |
| HW crypto engine             | stalled        | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv1](https://lore.kernel.org/all/20231107155532.3747113-1-clabbe@baylibre.com/), [working tree from Corentin Labbe](https://github.com/montjoie/linux/commits/rk2-crypto-v1/) |
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
| SFC (Flash Controller)       | {+ 6.7-rc1 +}  | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | {+ 6.16-rc1 +} | `n/a`          | DONE  |
| DFI                          | {+ 6.7-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE (DDR memory utilization for perf) |
| ADC                          | {+ 6.5-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.7-rc1 +}  | DONE  |
| Thermal ADC                  | {+ 6.4-rc1 +}  | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | {+ 6.16-rc1 +} | {+ 6.11-rc1 +} | DONE  |
| Watchdog                     | {+ 6.4-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| GPU                          | {+ 6.10-rc1 +} | {+ 6.13-rc1 +} | {+ 6.10-rc1 +} | {+ 6.16-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| NPU                          | {+ 6.18-rc1 +} | {- TODO -}     | {+ 6.18-rc1 +} | {+ 6.18-rc1 +} | {- TODO -}     | DONE  |
| ISP                          | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| RGA2                         | {+ 6.12-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| RGA3                         | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv3](https://lore.kernel.org/linux-rockchip/20260127-spu-rga3-v3-0-77b273067beb@pengutronix.de/) |
| HDMI Input                   | {+ 6.15-rc1 +} | `n/a`          | {+ 6.15-rc1 +} | {+ 6.16-rc1 +} | {+ 6.17-rc1 +} |       |
|  - CEC                       | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|  - Audio                     | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - HDCP                      | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| **Video Capture (VICAP)**    | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [RK3568 in v6.19](https://lore.kernel.org/all/aResANF6CFNo9C4w@valkosipuli.retiisi.eu/) |
|  - Digital Video Port (DVP)  | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          | Note: is there HW that exposes that? |
|  - MIPI CSI Hosts            | {+ 7.0-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PR for 7.0](https://lore.kernel.org/linux-media/aXCOTYy9xh6h5DX9@valkosipuli.retiisi.eu/) |
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
|  - **VDPU381**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [DT support in v7.0](https://lore.kernel.org/linux-rockchip/176798895637.3449720.6051032825613833368.b4-ty@sntech.de/) |
|   -- H.264                   | {+ 7.0-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PRv2 for 7.0](https://lore.kernel.org/linux-media/379e2cfb0ac6640936446b5e76dd24f854e7800c.camel@collabora.com/) |
|   -- H.265                   | {+ 7.0-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PRv2 for 7.0](https://lore.kernel.org/linux-media/379e2cfb0ac6640936446b5e76dd24f854e7800c.camel@collabora.com/) |
|   -- VP9                     | wip            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | WIP by Venkata Atchuta Bheemeswara Sarma Darbha |
|   -- AVS2                    | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU720**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                    | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU981**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- AV1                     | {+ 6.7-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|    - AV1 IOMMU               | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv11](https://lore.kernel.org/linux-rockchip/20260107101005.84039-1-benjamin.gaignard@collabora.com/) |

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux

RK3588 Improvements (pending)
=============================

 * Force color format support: [PATCHv7](https://lore.kernel.org/linux-rockchip/20260121-color-format-v7-0-ef790dae780c@collabora.com/)
 * Background color support: [PATCHv6](https://lore.kernel.org/linux-rockchip/20260129-rk3588-bgcolor-v6-0-c15f755a4055@collabora.com/)
 * HDMI VSI & SPD InfoFrames: [PATCHv2](https://lore.kernel.org/linux-rockchip/20260129-dw-hdmi-qp-iframe-v2-0-0157ad05232c@collabora.com/)
 * PCIe System PM support: [PATCHv3](https://lore.kernel.org/linux-rockchip/1744940759-23823-1-git-send-email-shawn.lin@rock-chips.com/)
 * PCIe slot reset on link down: [PATCHv6](https://lore.kernel.org/linux-pci/20250715-pci-port-reset-v6-0-6f9cce94e7bb@oss.qualcomm.com/)
 * Improved USB-C Orientation handling: [PATCHv2](https://lore.kernel.org/linux-rockchip/20250226103810.3746018-1-heiko@sntech.de/)
 * VOP VP clock reset support: [PATCHv3](https://lore.kernel.org/linux-rockchip/20241108185212.198603-1-detlev.casanova@collabora.com/)
 * Limit HDMI infoframes: [PATCHv1](https://lore.kernel.org/linux-rockchip/20250816-drm-limit-infoframes-v1-0-6dc17d5f07e9@oss.qualcomm.com/)
 * AV1 CDEF computation fix: [PATCHv2](https://lore.kernel.org/linux-rockchip/20251209103401.21943-1-benjamin.gaignard@collabora.com/)
 * AV1 tx mode bit fix: [PATCHv2](https://lore.kernel.org/linux-rockchip/20251209103417.21966-1-benjamin.gaignard@collabora.com/)
 * AV1 file info buffer size fix: [PATCHv1](https://lore.kernel.org/linux-rockchip/20260114090710.71473-1-benjamin.gaignard@collabora.com/)
 * Improve handling missing short/long term RPS in rkvdec: [PATCHv1](https://lore.kernel.org/linux-rockchip/20260123192244.1441637-1-detlev.casanova@collabora.com/)
 * VOP2 atomic uAPI cleanup: [PATCHv5](https://lore.kernel.org/linux-rockchip/20251215-vop2-atomic-fixups-v5-0-83463c075a8d@collabora.com/)
 * PCIe LTSSM tracepoint support: [PATCHv4](https://lore.kernel.org/linux-rockchip/1769047340-113287-1-git-send-email-shawn.lin@rock-chips.com/)
 * V4L2 stateless codec tracepoint support: [PATCHv1](https://lore.kernel.org/linux-rockchip/20260212162328.192217-1-detlev.casanova@collabora.com/)
 * VOP Mode Filtering: [PATCHv1](https://lore.kernel.org/linux-rockchip/20260116005953.286225-1-andyshrk@163.com/)
 * HDMI-RX EDID fix: [PATCHv1](https://lore.kernel.org/linux-rockchip/20260209061654.54757-1-ross@r-sc.ca/)

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
 * Unified `HIWORD_UPDATE` macros (6.18-rc1): [PATCHv3](https://lore.kernel.org/linux-rockchip/20250825-byeword-update-v3-0-947b841cdb29@collabora.com/)
 * Fix Thermal GRF warning (6.18-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/20250820-thermal-rockchip-grf-warning-v2-0-c7e2d35017b8@kernel.org/)
 * HDMI PHY fixes (6.19-rc1): [PATCH](https://lore.kernel.org/linux-rockchip/20251028-phy-hdptx-fixes-v1-0-ecc642a59d94@collabora.com/)
 * HDMI high color depth support (6.19-rc1): [PATCHv3](https://lore.kernel.org/linux-rockchip/20251021-rk3588-10bpc-v3-0-3d3eed00a6db@collabora.com/)
 * HDMI PHY 461.10125 MHz fix (7.0-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/20251221-phy-hdptx-pll-fix-v2-0-ae4abf7f75a1@collabora.com/)
 * HDMI PHY FRL support (7.0-rc1): [PATCHv6](https://lore.kernel.org/linux-rockchip/20260113-phy-hdptx-frl-v6-0-8d5f97419c0b@collabora.com/)
 * Expand S/PDIF Features needed for DP audio (7.0-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/177033773886.236064.14543193521688333504.b4-ty@kernel.org/)
 * HDMI-RX TF-A detection (7.0-rc1): [PATCHv3](https://lore.kernel.org/linux-rockchip/20251210160006.528997-1-dmitry.osipenko@collabora.com/)
 * Network GMAC cleanups (7.0-rc1): [PATCHv1](https://lore.kernel.org/linux-rockchip/aYMN2gZMfLPKuukG@shell.armlinux.org.uk/)
