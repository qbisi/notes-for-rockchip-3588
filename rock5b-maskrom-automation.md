# ROCK 5 Model B Boot automation

This document is applicable to the ROCK5 Model B (hardware version 1.42).


## Maskrom

The maskrom button can be pressed before booting to manually force the device
into maskrom mode and not boot from the flash devices. Maskrom is a special boot
mode which allows the device to be controlled over USB to e.g. flash an image to
the eMMC.


## Runtime

Before applying power to the board, pull the maskrom signal to 0V. Once the
board has booted to maskrom mode, return the maskrom signal to a floating state.
This can be done by pressing the maskrom button, or by implementing the modification
detailed below.


## Hardware modification

The maskrom switch connects the `BOOT_SARADC_IN0` net to ground, the modification
is designed to emulate pressing the switch. The `BOOT_SARADC_IN0` net is
connected to a high-impedance ADC pin on the rk3588. Any wires connected to this
switch may pick up noise from the environment and cause the boot mode to be
unstable. It is important to keep the wires short (e.g. less than 1m).

Since there is a pull-up on the `BOOT_SARADC_IN0` net, and the internal boot code
measures the voltage of the pin to choose a boot mode, it is also important to
keep the on-resistance of the switch circuit very low (e.g. less than 500 ohms)
to prevent a false boot mode. A relay or MOSFET should be used to pull the net
down; a BJT may be harder to bias correctly.

A relay can be used to emulate pressing the maskrom button but a solid-state
circuit with a MOSFET close to the device would be preferred to keep the loop
distance short and also to improve the lifetime of the test circuit as no
mechanical parts would be involved. This is out of the scope of this document
since it depends on the available hardware in your test lab.

![Maskrom Mod](img/rock5b-maskrom-mod.jpg)

The blue wire is connected to `J9510-2` which is the `BOOT_SARADC_IN0` net.
The black wire is connected to `J9510-1` which is the `0V` net.
