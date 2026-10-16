# USB recovery

USB recovery starts the CM4 from a host computer while leaving the microSD card installed. The independent STM32 controls the CM4 supply, boot signals, and USB routing, so the normal CM4 operating system does not need to be running.

## Recovery sequence

1. Shut down the CM4 operating system if it is still accessible, then turn off the CM4 supply.
2. The controller selects the recovery USB path, asserts the CM4 recovery-boot signal, and sequences CM4 power and reset.
3. The host computer detects the CM4 USB boot ROM through the onboard recovery hub.
4. Raspberry Pi's `rpiboot` loads a USB storage gadget into CM4 RAM.
5. The gadget exposes the microSD card to the host computer.
6. After safely ejecting the card on the host, the controller powers down the CM4, restores the normal USB path and boot selection, and starts it again.

This is a functional sequence, not an executable procedure. The host utility and gadget-preparation scripts used during development are not distributed here. `rpiboot` alone does not perform the board-specific controller commands.

## What was tested

On the development prototype with controller v2.04 and macOS:

- CM4 recovery boot and detection by the host.
- A 64 GB microSD card exposed as read-only USB storage.
- Safe ejection followed by normal microSD boot and SSH access.

The recovery round trip used a Mac port advertising 1.5 A, with the USB-A ports empty and a limited-current test mode enabled explicitly. After normal boot was restored, current undervoltage/throttling flags were clear, but historical flags were set. These results do not establish full-load operation from the intended 5 V / 3 A source.

The STM32 does not transfer the SD data itself. The CM4 runs the RAM-loaded storage software. No prepared RAM image is included in this repository.

Rewriting the microSD card, interruption during a write, and boot after rewriting have not been tested. Read-only validation does not establish those behaviors.

Upstream boot software: [Raspberry Pi usbboot](https://github.com/raspberrypi/usbboot).
