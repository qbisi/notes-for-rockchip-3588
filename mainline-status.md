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
|  -- HDMI 4K60 support        | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv5](https://lore.kernel.org/linux-rockchip/20260426-dw-hdmi-qp-scramb-v5-0-d778e70c317b@collabora.com/) |
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
| - DP1.4 USB-C AltMode        | WIP            | `n/a`          | {- TODO -}     | {- TODO -}     | {- TODO -}     | [PATCHv2](https://lore.kernel.org/linux-rockchip/20260501-synopsys-dw-dp-improvements-v2-0-d7e7f6bac77f@collabora.com/) |
|  -- DP Bridge                | {+ 6.18-rc1 +} | `n/a`          | {- TODO -}     | {- TODO -}     | {- TODO -}     | DONE, some DT binding updates required for proper USB-C AltMode support |
|    -- Audio                  | sent           | `n/a`          | {- TODO -}     | {- TODO -}     | {- TODO -}     | [PATCHv2](https://lore.kernel.org/linux-rockchip/20260501-synopsys-dw-dp-improvements-v2-0-d7e7f6bac77f@collabora.com/) |
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
| DMC                          | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          | Dynamic Memory Controller (memory frequency scaling) |
| ADC                          | {+ 6.5-rc1 +}  | {+ 6.6-rc1 +}  | {+ 6.5-rc1 +}  | {+ 6.16-rc1 +} | {+ 6.7-rc1 +}  | DONE  |
| Thermal ADC                  | {+ 6.4-rc1 +}  | {+ 6.11-rc1 +} | {+ 6.11-rc1 +} | {+ 6.16-rc1 +} | {+ 6.11-rc1 +} | DONE  |
| Watchdog                     | {+ 6.4-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| GPU                          | {+ 6.10-rc1 +} | {+ 6.13-rc1 +} | {+ 6.10-rc1 +} | {+ 6.16-rc1 +} | {+ 6.10-rc1 +} | DONE  |
| NPU                          | {+ 6.18-rc1 +} | {- TODO -}     | {+ 6.18-rc1 +} | {+ 6.18-rc1 +} | {- TODO -}     | DONE  |
| ISP                          | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [RFCv1](https://lore.kernel.org/linux-media/20260424175853.638202-1-paul.elder@ideasonboard.com/) |
| RGA2                         | {+ 6.12-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
| RGA3                         | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv5](https://lore.kernel.org/linux-rockchip/20260428-spu-rga3-v5-0-eb7f5d019d86@pengutronix.de/) |
| HDMI Input                   | {+ 6.15-rc1 +} | `n/a`          | {+ 6.15-rc1 +} | {+ 6.16-rc1 +} | {+ 6.17-rc1 +} |       |
|  - CEC                       | {+ 6.15-rc1 +} | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|  - Audio                     | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - HDCP                      | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
| **Video Capture (VICAP)**    | sent           | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv3](https://lore.kernel.org/linux-rockchip/20250430-rk3588-vicap-v3-0-e38e428868cc@collabora.com/) |
|  - Digital Video Port (DVP)  | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          | Note: is there HW that exposes that? |
|  - MIPI CSI Hosts            | {+ 7.0-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv5 with DT updates for RK3588](https://lore.kernel.org/linux-rockchip/20260305-rk3588-csi2rx-v5-0-3b7061d043ea@collabora.com/) |
|  - MUX/TOISP                 | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
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
|  - **VDPU381**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|   -- H.264                   | {+ 7.0-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE, missing multi-core support (see improvements section) |
|   -- H.265                   | {+ 7.0-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE, missing multi-core support (see improvements section) |
|   -- VP9                     | wip            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [WIP by Venkata Atchuta Bheemeswara Sarma Darbha](https://github.com/dvab-sarma/android_kernel_rk_opi/commit/aa00b89b6bbfd7570e459172417e2e72921689f4) |
|   -- AVS2                    | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU720**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- JPEG                    | {- TODO -}     | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|  - **VDPU981**               | `n/a`          | `n/a`          | `n/a`          | `n/a`          | `n/a`          |       |
|   -- AV1                     | {+ 6.7-rc1 +}  | `n/a`          | `n/a`          | `n/a`          | `n/a`          | DONE  |
|    - AV1 IOMMU               | WIP            | `n/a`          | `n/a`          | `n/a`          | `n/a`          | [PATCHv14](https://lore.kernel.org/linux-rockchip/20260415072349.44237-1-benjamin.gaignard@collabora.com/) |

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux

RK3588 Improvements (pending)
=============================

 * NPU: Support standalone DPU/PPU tasks and pipelined workloads: [PATCHv1](https://lore.kernel.org/linux-kernel/20260217-accel-rocket-clean-base-v1-0-d72354325a25@r-sc.ca/)
 * Force color format support: [PATCHv14](https://lore.kernel.org/linux-rockchip/20260423-color-format-v14-0-449a419ccbd4@collabora.com/)
 * PCIe System PM support: [PATCHv5](https://lore.kernel.org/linux-rockchip/20260316-rockchip-pcie-system-suspend-v5-0-5bb5ad37d643@collabora.com/)
 * PCIe slot reset on link down: [PATCHv6](https://lore.kernel.org/linux-pci/20250715-pci-port-reset-v6-0-6f9cce94e7bb@oss.qualcomm.com/)
 * PCIe SSC tuning cleanup in naneng combphy: [PATCHv2](https://lore.kernel.org/linux-rockchip/1772696450-139583-1-git-send-email-shawn.lin@rock-chips.com/)
 * Improved USB-C Orientation handling: [PATCHv2](https://lore.kernel.org/linux-rockchip/20250226103810.3746018-1-heiko@sntech.de/)
 * VOP VP clock reset support: [PATCHv3](https://lore.kernel.org/linux-rockchip/20241108185212.198603-1-detlev.casanova@collabora.com/)
 * Limit HDMI infoframes: [PATCHv1](https://lore.kernel.org/linux-rockchip/20250816-drm-limit-infoframes-v1-0-6dc17d5f07e9@oss.qualcomm.com/)
 * V4L2 stateless codec tracepoint support: [PATCHv1](https://lore.kernel.org/linux-rockchip/20260212162328.192217-1-detlev.casanova@collabora.com/)
 * HDMI PHY clock fixes: [PATCHv1](https://lore.kernel.org/linux-rockchip/20260227-hdptx-clk-fixes-v1-0-f998f2762d0f@collabora.com/)
 * HDMI-RX EDID fix: [PATCHv2](https://lore.kernel.org/linux-rockchip/20260325105742.63236-1-dmitry.osipenko@collabora.com/)
 * USBDP PHY fixes for DisplayPort usage: [PATCHv4](https://lore.kernel.org/linux-rockchip/20260428-rockchip-usbdp-cleanup-v4-0-7775671ece22@collabora.com/)
 * TCPM fix for some USB-C DP adapters: [PATCHv4](https://lore.kernel.org/linux-usb/20260429-tcpm-discover-modes-nak-fix-v4-1-75945d0ed30f@collabora.com/)
 * Rockchip Camera Interface fixes: [PATCHv2](https://lore.kernel.org/linux-media/20260216-rkcif-fixes-v2-0-ee40931fe0ff@collabora.com/)
 * I2C SCL Debounce support: [PATCHv2](https://lore.kernel.org/linux-rockchip/20260321105146.7419-1-linux.amoon@gmail.com/)
 * eMMC driver platform data refactoring: [PATCHv2](https://lore.kernel.org/linux-rockchip/1774620875-18258-1-git-send-email-shawn.lin@rock-chips.com/)
 * eMMC driver DLL clock quirk: [PATCHv3](https://lore.kernel.org/linux-rockchip/1775632729-22841-1-git-send-email-shawn.lin@rock-chips.com/)
 * Move rkvdec from bitfield to bitwriter: [PATCHv3](lore.kernel.org/linux-rockchip/20260402-rkvdec-use-bitwriter-v3-0-2072474ceaf4@collabora.com/)
 * SAI slot width fix: [PATCHv1](https://lore.kernel.org/linux-rockchip/5445638.31r3eYUQgx@workhorse/)
 * VDPU381 multi-core support for H.264/H.265: [PATCHv1](https://lore.kernel.org/linux-media/20260409-rkvdec-multicore-v1-0-62b316abf0f7@collabora.com/)

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
 * VOP2 atomic uAPI cleanup (7.0-rc1): [PATCHv5](https://lore.kernel.org/linux-rockchip/20251215-vop2-atomic-fixups-v5-0-83463c075a8d@collabora.com/)
 * Expand S/PDIF Features needed for DP audio (7.0-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/177033773886.236064.14543193521688333504.b4-ty@kernel.org/)
 * HDMI-RX TF-A detection (7.0-rc1): [PATCHv3](https://lore.kernel.org/linux-rockchip/20251210160006.528997-1-dmitry.osipenko@collabora.com/)
 * Network GMAC cleanups (7.0-rc1): [PATCHv1](https://lore.kernel.org/linux-rockchip/aYMN2gZMfLPKuukG@shell.armlinux.org.uk/)
 * AV1 CDEF computation fix (7.0-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/20251209103401.21943-1-benjamin.gaignard@collabora.com/)
 * AV1 tx mode bit fix (7.0-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/20251209103417.21966-1-benjamin.gaignard@collabora.com/)
 * AV1 file info buffer size fix (7.0-rc1): [PATCHv1](https://lore.kernel.org/linux-rockchip/20260114090710.71473-1-benjamin.gaignard@collabora.com/)
 * Improve handling missing short/long term RPS in rkvdec (7.0-rc6): [PATCHv1](https://lore.kernel.org/linux-rockchip/20260123192244.1441637-1-detlev.casanova@collabora.com/)
 * Synopsys CSI2 receiver fixes (7.0-rc6): [PATCHv1](https://lore.kernel.org/linux-media/20260216-snps-csi2rx-v1-0-747bc7408f87@collabora.com/)
 * USB-C mux fixes for Rockchip USBDP (7.1-rc1): [PATCHv2](https://lore.kernel.org/linux-usb/20260223-typec-mux-duplication-fix-v2-0-0402fefc222e@collabora.com/)
 * fusb302 support for DRM (7.1-rc1): [PATCHv1](https://lore.kernel.org/linux-usb/20260310-fusb302-drm-dp-hpd-bridge-v1-1-ffd41ef9afe3@collabora.com/)
 * Background color support (7.1-rc1): [PATCHv8](https://lore.kernel.org/linux-rockchip/20260303-rk3588-bgcolor-v8-0-fee377037ad1@collabora.com/)
 * VOP Mode Filtering (7.1-rc1): [PATCHv2](https://lore.kernel.org/linux-rockchip/20260117020738.294825-1-andyshrk@163.com/)
 * HDMI VSI & SPD InfoFrames (7.1-rc1): [PATCHv2](https://lore.kernel.org/lkml/20260129-dw-hdmi-qp-iframe-v2-0-0157ad05232c@collabora.com/)
 * PCIe LTSSM tracepoint support (7.1-rc1): [PATCHv5](https://lore.kernel.org/linux-rockchip/1774403912-210670-1-git-send-email-shawn.lin@rock-chips.com/)
 * Use dynamic GPIO numberspace (7.1-rc1): [PATCHv1](https://lore.kernel.org/linux-rockchip/1774864401-177149-1-git-send-email-shawn.lin@rock-chips.com/)
 * Hynetek HUSB311 support (7.1-rc1): [PATCHv4](https://lore.kernel.org/lkml/20260318-husb311-v4-0-69e029255430@flipper.net/)
 * Add support for I2S MCLK output gate clocks (7.2-rc1): [PATCHv3](https://lore.kernel.org/linux-rockchip/20260320-rk3588-mclk-gate-grf-v3-0-980338eacd2c@superkali.me/)
