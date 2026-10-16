# Release preparation

This repository currently contains prototype documentation and presentation images. It does not contain a firmware binary, host utility, prepared recovery image, or manufacturing package.

## Before the first firmware release

- [ ] Match the photographed PCB to the R2 design and the tested v2.04 controller configuration.
- [ ] Verify physical header orientation and publish the J6/J7 pinout and programming sequence.
- [ ] Decide how users will obtain the controller host utility needed for PC-controlled startup and recovery.
- [ ] Prepare the current CM4 Carrier Board's editable hardware design files and firmware source for the planned open release.
- [ ] Assemble the corresponding libopencm3 source, notices, and reproducible build instructions for the exact binary.
- [ ] Select the reuse terms for project-owned documentation and images, and finalize the firmware distribution terms.

## Validation still open

- microSD rewriting over USB recovery, including boot after a rewrite.
- USB-A peripheral current, simultaneous peripheral operation, and sustained traffic.
- Long-duration operation and power behavior under load.

Recorded successful tests are summarized in the [README](../README.md#validation-status). No support for other PCB revisions is established by those results.

## Future hardware

CM5 support is planned for a future hardware revision. It has not been validated on the current prototype, and no release date has been set. R7's release plans remain undecided.
