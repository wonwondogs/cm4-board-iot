# Startup and power

## What you need

- A Raspberry Pi Compute Module 4 Lite and suitable mounting hardware.
- A microSD card prepared for the selected CM4 operating system.
- A USB-C source advertising 5 V / 3 A and a suitable cable.
- For serial diagnostics: a 3.3 V USB-UART adapter and a fitted UART header.

The controller firmware and PCB revision must be compatible. The public firmware package is still in preparation; see the [firmware notes](../firmware/README.md).

## Standalone startup

1. Disconnect power. Install and secure the CM4, then insert the prepared microSD card.
2. Leave the STM32 BOOT/RESET jumper open. Begin with the USB-A ports empty.
3. Connect the USB-C supply.
4. With v2.04, the controller permits automatic startup after approximately five seconds when it detects a 3 A source and no USB host has configured the controller.
5. Confirm operating-system startup through the configured console or network connection. An enabled power rail alone does not confirm a successful boot.

The 5 V / 3 A input is shared by the CM4 and all attached peripherals. USB-A load testing and long-duration operation are not yet complete.

## Connection to a host computer

A configured USB host prevents the standalone automatic-start path. Development used a separate host utility to request normal startup, recovery startup, and power-off. That utility is not included in this repository, so the public package does not yet provide an end-to-end procedure for PC-controlled startup or recovery.

## Shutdown

Shut down the CM4 operating system and wait for shutdown to finish before removing power. A controller power-off command cuts the supply and does not perform an operating-system shutdown.
