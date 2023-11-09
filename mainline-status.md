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

|                          | Phabricator                                        | SoC      | Rock Pi 5A | Rock Pi 5B | EVB1    | Notes |
| ------------------------ | -------------------------------------------------- | -------- | ---------- | ---------- | ------- | ----- |
| PHY naneng combphy       | [T39901](https://phabricator.collabora.com/T39901) | 6.4-rc1  | sent       | sent       | 6.7-rc1 | DONE (except for enabling board-level USB3)
| PHY SNPS PCIe3           | [T43707](https://phabricator.collabora.com/T43707) | 6.6-rc1  | n/a        | 6.7-rc1    | 6.7-rc1 | DONE
| PHY inno usb2            | [T39908](https://phabricator.collabora.com/T39908) | 6.6-rc1  | 6.6-rc1    | 6.6-rc1    | 6.6-rc1 | DONE
| PHY usbdp                | [T41615](https://phabricator.collabora.com/T41615) | WIP      | ready      | ready      | ready   | PHY for USB3 Dual Role
| PMIC (rk806)             | [T36154](https://phabricator.collabora.com/T36154) | n/a      | 6.6-rc1    | 6.5-rc1    | 6.5-rc1 | DONE (Power Management IC used by all known RK3588 boards)
| I2C Regulator (rk8602)   | [T41143](https://phabricator.collabora.com/T41143) | n/a      | 6.6-rc1    | 6.4-rc1    | n/a     | DONE (Extra Regulator chip used by some RK3588 boards)
| USB-PD Controller        | [T40098](https://phabricator.collabora.com/T40098) | n/a      | n/a        | ready      | ready   |
| cpufreq                  | [T41636](https://phabricator.collabora.com/T41636) | WIP      | WIP        | WIP        | WIP     |
| PCIe3                    | [T43707](https://phabricator.collabora.com/T43707) | 6.6-rc1  | n/a        | 6.7-rc1    | 6.7-rc1 | DONE
| PCIe2                    | [T39901](https://phabricator.collabora.com/T39901) | 6.6-rc1  |            | 6.7-rc1    | 6.7-rc1 | DONE
| Ethernet                 | [T35212](https://phabricator.collabora.com/T35212) | 6.1-rc1  | 6.3-rc1    | n/a        | 6.3-rc1 | DONE (Rock 5B does not use SoC ethernet. It has a PCIe network card instead)
| USB 2                    | [T39908](https://phabricator.collabora.com/T39908) | 6.5-rc1  | 6.6-rc1    | 6.6-rc1    | 6.6-rc1 | DONE
| USB 3 DRD                | [T41615](https://phabricator.collabora.com/T41615) | ready    | ready      | ready      | ready   | waiting for usbdp PHY
| USB 3 Host               | [T41616](https://phabricator.collabora.com/T41616) | 6.7-rc1  | sent       | sent       | n/a     | [Rock 5 DT patches](https://lore.kernel.org/lkml/20231106155934.80838-1-sebastian.reichel@collabora.com/)
| USB-C                    | [T41615](https://phabricator.collabora.com/T41615) | n/a      | n/a        | ready      | ready   |
| eMMC                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  | 6.3-rc1    | 6.3-rc1    | 6.3-rc1 | DONE
| SD Card                  | [T39448](https://phabricator.collabora.com/T39448) | 6.4-rc1  | 6.6-rc1    | 6.5-rc1    | n/a     | DONE
| SDIO                     | [T41465](https://phabricator.collabora.com/T41465) | 6.5-rc1  | n/a        | 6.7-rc1    | n/a     | DONE
| SATA                     | [T41470](https://phabricator.collabora.com/T41470) | 6.5-rc1  | n/a        | n/a        | 6.6-rc1 | DONE
| Timer                    | [T41468](https://phabricator.collabora.com/T41468) | 6.4-rc1  | n/a        | n/a        | n/a     | DONE
| OTP                      | [T41964](https://phabricator.collabora.com/T41964) | 6.5-rc1  | n/a        | n/a        | n/a     | DONE
| Display Controller       |                                                    |          |            |            |         |
| - HDMI                   | [T36469](https://phabricator.collabora.com/T36469) |          |            |            |         | WIP
|   - HDMI Audio           |                                                    |          |            |            |         |
|   - HDCP                 |                                                    |          |            |            |         |
| - DSI                    |                                                    |          |            |            |         |
| - DP1.4 USB-C AltMode    |                                                    |          |            |            |         |
| M2 E                     |                                                    | n/a      |            |            | n/a     | requires SDIO, PCIe2, I2S, UART, I2C, USB3; Rock 5B has partial support in v6.7-rc1
| M2 M                     |                                                    | n/a      | n/a        | 6.7-rc1    | n/a     | DONE
| Headphone Jack Playback  | [T40849](https://phabricator.collabora.com/T40849) | n/a      | 6.6-rc1    | 6.4-rc1    |         |
| Headphone Jack Record    | [T40849](https://phabricator.collabora.com/T40849) | n/a      | 6.6-rc1    | 6.4-rc1    |         |
| Real Time Clock (RTC)    | [T41459](https://phabricator.collabora.com/T41459) | n/a      | n/a        | 6.4-rc1    | 6.3-rc1 | DONE
| HW crypto engine         |                                                    | sent     | n/a        | n/a        | n/a     | [PATCHv1](https://lore.kernel.org/all/20231107155532.3747113-1-clabbe@baylibre.com/)
| Random Number Generator  |                                                    |          |            |            |         |
| UART                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  | 6.3-rc1    | 6.3-rc1    | 6.3-rc1 | DONE
| GPIO                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  | n/a        | n/a        | n/a     | DONE
| Pinmux                   | [T34481](https://phabricator.collabora.com/T34481) | 5.19-rc1 | n/a        | n/a        | n/a     | DONE
| Interrupts               | [T34481](https://phabricator.collabora.com/T34481) | 6.3-rc1  | n/a        | n/a        | n/a     | DONE
| GICv3 ITS support        | [T40845](https://phabricator.collabora.com/T40845) | 6.4-rc1  | n/a        | n/a        | n/a     | DONE
| PWM                      | [T34481](https://phabricator.collabora.com/T34481) | 6.3-rc1  | n/a        | n/a        | n/a     | DONE
| PWM FAN                  |                                                    | n/a      | 6.6-rc1    | 6.4-rc1    | n/a     | DONE
| SPI                      | [T36154](https://phabricator.collabora.com/T36154) | 6.1-rc1  | n/a        | n/a        | n/a     | DONE
| I2C                      | [T36154](https://phabricator.collabora.com/T36154) | 6.0-rc1  | n/a        | n/a        | n/a     | DONE
| I2S                      | [T40849](https://phabricator.collabora.com/T40849) | 6.2-rc1  | 6.6-rc1    | 6.4-rc1    |         | DONE (except for EVB1)
| CAN                      |                                                    |          |            |            |         |
| SPDIF                    |                                                    |          |            |            |         |
| SFC (Flash Controller)   |                                                    |          |            |            |         |
| OTP Memory               | [T41964](https://phabricator.collabora.com/T41964) | 6.5-rc1  | n/a        | n/a        | n/a     | DONE
| DFI                      |                                                    | 6.7-rc1  | n/a        | n/a        | n/a     | DONE (DDR memory utilization for perf)
| ADC                      | [T41456](https://phabricator.collabora.com/T41456) | 6.5-rc1  | 6.6-rc1    | 6.5-rc1    | 6.7-rc1 | DONE
| Thermal ADC              | [T36830](https://phabricator.collabora.com/T36830) | 6.4-rc1  | n/a        | n/a        | n/a     | pending patch to enable it at SoC level
| Watchdog                 | [T41179](https://phabricator.collabora.com/T41179) | 6.4-rc1  | n/a        | n/a        | n/a     | DONE
| GPU                      | [T37258](https://phabricator.collabora.com/T37258) |          |            |            |         | [PATCHv2](https://lore.kernel.org/all/20230809165330.2451699-1-boris.brezillon@collabora.com/), [Blog Post](https://www.collabora.com/news-and-blog/news-and-events/pancsf-a-new-drm-driver-for-mali-csf-based-gpus.html)
| Multimedia Codecs        |                                                    |          |            |            |         |
|  - ISP                   |                                                    |          |            |            |         |
|  - RKVDEC                |                                                    |          | n/a        | n/a        | n/a     |
|  - MIPI CSI              |                                                    |          |            |            |         |
|  - HDMI Input            | [T42207](https://phabricator.collabora.com/T42207) |          | n/a        |            |         | WIP
|    - CEC                 | [T42207](https://phabricator.collabora.com/T42207) |          | n/a        | n/a        | n/a     | WIP
|    - Audio               |                                                    |          |            |            |         |
|    - HDCP                |                                                    |          |            |            |         |
|  - AV1                   | [T38796](https://phabricator.collabora.com/T38796) | 6.7-rc1  | n/a        | n/a        | n/a     | DONE

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux
