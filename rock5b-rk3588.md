Radxa Rock 5b rk3588 board
==============================

The official Radxa page is [here](https://wiki.radxa.com/Rock5/5b)

Internal RK3588 documentation (datasheets, schematics) is available [here](https://share.collabora.com/index.php/apps/files/?dir=/Collabora/Datasheets/Rockchip/RK3588&fileid=2410201)

## Required hardware
The board comes in a box without any accessories.

### Power
To power it up, a type C USB cable is required. It should deliver at least 26 W power.

Tested working setups (in U-Boot, TBD at higher consumption):
 * Lenovo laptop charger (type C)
 * USB type C -> type C (from e.g. a laptop dockstation)

### Serial

A 3.3V capable USB-to-serial cable is required to connect to the serial. The pins are
pictured on the Radxa wiki. The baud rate is 1500000 so a cable that can
sustain this baud rate is required, e.g. FTDI, or CH340. CP210x-based ones or
counterfeit CH340 ones will not be able to do this baudrate!

**WARNING** if you connect a 5 V serial cable to this board, you risk to permanently damage it. Caution is advised.

### Maskrom

To put the board into maskrom mode, hold the maskrom button while applying power. Depending
on the board revision, the button is in different places.

For board revision `V1.42`:

![Maskrom](img/rock5b-maskrom-v1.42.jpg)

For board revision `V1.3`:

![Maskrom](img/rock5b-maskrom-v1.3.jpg)
