RK3588 Mainline Kernel support
==============================

|                          | Phabricator                                        | SoC      | Rock Pi 5A | Rock Pi 5B | EVB1    | Notes |
| ------------------------ | -------------------------------------------------- | -------- | ---------- | ---------- | ------- | ----- |
| PHY naneng combphy       | [T39901](https://phabricator.collabora.com/T39901) | ready    |            | ready      |         | PHY for PCIe2/USB3 host/SATA, [PATCHv2](https://lore.kernel.org/lkml/20230314135555.44162-1-lucas.tanure@collabora.com/)
| PHY inno usb2            | [T39908](https://phabricator.collabora.com/T39908) | sent     |            | ready      | ready   | PHY for USB2 (also used by USB3) [PATCHv2](https://lore.kernel.org/all/20230403202307.120562-1-sebastian.reichel@collabora.com/)
| PHY usbdp                | [T41615](https://phabricator.collabora.com/T41615) |          |            |            |         | PHY for USB3 Dual Role
| PMIC (rk806)             | [T36154](https://phabricator.collabora.com/T36154) | n/a      |            |            |         | [PATCHv7](https://lore.kernel.org/all/20230307153617.643260-1-sebastian.reichel@collabora.com/)
| I2C Regulator (rk8602)   | [T41143](https://phabricator.collabora.com/T41143) | n/a/     |            |            | n/a     |
| USB-PD Controller        | [T40098](https://phabricator.collabora.com/T40098) | n/a      |            |            |         |
| cpufreq                  | [T36830](https://phabricator.collabora.com/T36830) |          |            |            | WIP     | EVB1 supported in sre's branch
| PCIe3                    |                                                    |          |            |            |         | [driver PATCHv5](https://lore.kernel.org/all/5bec43fe-ff81-bc68-7b62-9e605b7e1f42@omnom.net/) , [Rock5b RFCv1](https://lore.kernel.org/all/cover.1675498628.git.wqu@suse.com/)
| PCIe2                    | [T39901](https://phabricator.collabora.com/T39901) | ready    |            | ready      |         | [PATCHv2](https://lore.kernel.org/all/20230314135555.44162-1-lucas.tanure@collabora.com/)
| Ethernet                 | [T35212](https://phabricator.collabora.com/T35212) | 6.1-rc1  | 6.3-rc1    | n/a        | 6.3-rc1 | DONE (Rock 5B does not use SoC ethernet. It has a PCIe network card instead)
| USB 2                    | [T39908](https://phabricator.collabora.com/T39908) | sent     |            | ready      | ready   | [PATCHv1](https://lore.kernel.org/all/20230331163148.5863-1-sebastian.reichel@collabora.com/)
| USB 3 DRD                | [T41615](https://phabricator.collabora.com/T41615) |          |            |            |         | https://github.com/neggles/linux-quartz64/issues/1
| USB 3 Host               | [T41616](https://phabricator.collabora.com/T41616) |          |            |            |         |
| USB-C                    | [T41615](https://phabricator.collabora.com/T41615) | n/a      |            |            |         |
| eMMC                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  | 6.3-rc1    | 6.3-rc1    | 6.3-rc1 | DONE
| SD Card                  | [T39448](https://phabricator.collabora.com/T39448) | 6.4-rc1  | ready      | ready      |         | [SoC support](https://lore.kernel.org/all/20230213152740.359055-1-lucas.tanure@collabora.com/), Rock Pi 5A/B support is working in local integration branch, but depends on mainline rk806 support
| SDIO                     | [T41465](https://phabricator.collabora.com/T41465) |          |            |            | n/a     |
| SATA                     | [T41470](https://phabricator.collabora.com/T41470) |          | n/a        | n/a        |         |
| Timer                    | [T41468](https://phabricator.collabora.com/T41468) |          |            |            |         |
| Display Controller       |                                                    |          |            |            |         |
| - HDMI                   | [T36469](https://phabricator.collabora.com/T36469) |          |            |            |         |
|   - HDMI Audio           |                                                    |          |            |            |         |
| - DSI                    |                                                    |          |            |            |         |
| - DP1.4 USB-C AltMode    |                                                    |          |            |            |         |
| M2 E                     |                                                    | n/a      |            |            | n/a     | requires SDIO, PCIe2, I2S, UART, I2C, USB3
| M2 M                     |                                                    | n/a      | n/a        |            | n/a     | requires PCIe3
| Headphone Jack Playback  | [T40849](https://phabricator.collabora.com/T40849) | n/a      |            | sent       |         | [PATCHv1](https://lore.kernel.org/lkml/20230315114806.3819515-1-cristian.ciocaltea@collabora.com/)
| Headphone Jack Record    | [T40849](https://phabricator.collabora.com/T40849) | n/a      |            | sent       |         | [PATCHv1](https://lore.kernel.org/lkml/20230315114806.3819515-1-cristian.ciocaltea@collabora.com/)
| Real Time Clock (RTC)    | [T41459](https://phabricator.collabora.com/T41459) | n/a      |            |            | 6.3-rc1 |
| HW crypto engine         |                                                    |          |            |            |         | [RFTv1](https://lore.kernel.org/all/20220927080048.3151911-1-clabbe@baylibre.com/)
| Random Number Generator  |                                                    |          |            |            |         |
| UART                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  | 6.3-rc1    | 6.3-rc1    | 6.3-rc1 | DONE
| GPIO                     | [T34481](https://phabricator.collabora.com/T34481) | 6.0-rc1  |            |            |         |
| Pinmux                   | [T34481](https://phabricator.collabora.com/T34481) | 5.19-rc1 | n/a        | n/a        | n/a     |
| Interrupts               | [T34481](https://phabricator.collabora.com/T34481) | 6.3-rc1  | n/a        | n/a        | n/a     |
| GICv3 ITS support        | [T40845](https://phabricator.collabora.com/T40845) |          | n/a        | n/a        | n/a     | required for PCIe, needs support from Rockchip, see [discussion from this thread](https://yhbt.net/lore/all/874kg0q6lc.wl-maz@kernel.org/)
| PWM                      | [T34481](https://phabricator.collabora.com/T34481) | 6.3-rc1  |            |            |         |
| SPI                      | [T36154](https://phabricator.collabora.com/T36154) | 6.1-rc1  |            |            |         |
| I2C                      | [T36154](https://phabricator.collabora.com/T36154) | 6.0-rc1  |            |            |         |
| I2S                      | [T40849](https://phabricator.collabora.com/T40849) | 6.2-rc1  |            | sent       |         | [driver patch (merged)](https://lore.kernel.org/all/20221025124132.399729-1-frattaroli.nicolas@gmail.com/), [DTS series](https://lore.kernel.org/lkml/20230321215624.78383-1-cristian.ciocaltea@collabora.com/)
| CAN                      |                                                    |          |            |            |         |
| SPDIF                    |                                                    |          |            |            |         |
| SFC (Flash Controller)   |                                                    |          |            |            |         |
| ADC                      | [T41456](https://phabricator.collabora.com/T41456) |          |            |            |         |
| Thermal ADC              | [T36830](https://phabricator.collabora.com/T36830) |          | n/a        | n/a        | n/a     | [PATCHv3](https://lore.kernel.org/all/20230308112253.15659-1-sebastian.reichel@collabora.com/)
| Watchdog                 | [T41179](https://phabricator.collabora.com/T41179) |          | n/a        | 6.4-rc1    | n/a     | [DONE](https://lore.kernel.org/lkml/20230328210048.195124-1-shreeya.patel@collabora.com/T/)
| GPU                      | [T37258](https://phabricator.collabora.com/T37258) |          |            |            |         | [Blog Post](https://www.collabora.com/news-and-blog/news-and-events/pancsf-a-new-drm-driver-for-mali-csf-based-gpus.html)
| Multimedia Codecs        |                                                    |          |            |            |         |
|  - ISP                   |                                                    |          |            |            |         |
|  - RKVDEC                |                                                    |          |            |            |         |
|  - MIPI CSI              |                                                    |          |            |            |         |
|  - HDMI Input            |                                                    |          |            |            |         |
|  - AV1                   | [T38796](https://phabricator.collabora.com/T38796) |          |            |            |         |

Git branch with basic rk3588 hardware enablement (**WILL BE REBASED!**):
 * https://gitlab.collabora.com/hardware-enablement/rockchip-3588/linux
