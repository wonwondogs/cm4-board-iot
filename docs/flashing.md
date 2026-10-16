# STM32 programming

## Target

| Item | Value |
| --- | --- |
| Controller | STM32F042K6 |
| Candidate application | v2.04 |
| Application flash base | `0x08000000` |
| Public binary | Not released yet |

The controller application runs on the STM32. It is separate from the CM4 operating-system image stored on microSD.

## Programming interfaces

The development prototype was programmed through the STM32 ROM USB DFU bootloader. USB communication with the controller and a return to ROM DFU were verified on hardware. J6 provides physical BOOT0/reset access, and J7 provides SWD access for programming or recovery.

J6 is unrelated to the CM4's USB recovery boot mode. Do not bridge header pins based on the presentation photograph; a revision-specific wiring diagram is required.

## Release procedure

The public programming guide still needs the verified J6/J7 pinout, the exact bootloader-entry sequence, and commands checked against the release binary. These will be supplied with the firmware package. The development record must not be treated as a complete flashing procedure for other board revisions.

The release will include a SHA-256 checksum. The current candidate checksum and compatibility status are listed in the [firmware notes](../firmware/README.md).
