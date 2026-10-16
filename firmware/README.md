# STM32 firmware

The firmware controls CM4 power sequencing, boot selection, USB routing, and the REC indicator. It also reports voltage and power-state information over USB.

## Candidate version

| Item | Value |
| --- | --- |
| MCU | STM32F042K6 |
| Version | 2.04 |
| Intended release filename | `controller-v2.04.bin` |
| Size | 9,416 bytes |
| SHA-256 | `f696e698a1d9673405451aa3b39e5e08a493be0a1ddb5aab7ebd5bc3026333f2` |
| Compatibility | Development prototype tested; photographed PCB revision check pending |
| Distribution | No binary released yet |

The development record includes a matching flash readback, CM4 USB recovery, read-only microSD access from macOS, and return to normal boot. See [USB recovery](../docs/usb-recovery.md) for the tested scope.

In v2.04, undervoltage detected after startup produces a warning while CM4 power remains on. Other fault conditions, including overvoltage, can still stop the supply. The ADC readings are firmware telemetry and have not been calibrated against an external meter.

## Release contents

The planned open release for this CM4 Carrier Board will include its firmware source code alongside the binary, checksum, release notes, supported PCB revision, programming instructions, and required third-party redistribution materials. The source code and binary are not included in this documentation repository yet. R7's release plans are undecided.

The firmware links libopencm3 statically. The planned source package will include the corresponding library source, license notices, and build instructions. These must be checked against the distributed binary; license texts alone do not complete that package. See [licensing status](../LICENSING.md).

## Host-side requirements

Standalone startup and host-controlled operation have different requirements; see [startup and power](../docs/getting-started.md). The controller command utility and recovery preparation scripts used during development are not currently distributed here.

## Related documentation

- [Programming interfaces](../docs/flashing.md)
- [USB recovery](../docs/usb-recovery.md)
- [Release preparation](../docs/release-status.md)
