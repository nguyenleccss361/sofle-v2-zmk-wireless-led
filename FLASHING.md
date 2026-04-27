# Sofle ZMK Flashing Guide

This repo builds 3 UF2 files:

- `sofle_left-nice_nano_v2-zmk.uf2`
- `sofle_right-nice_nano_v2-zmk.uf2`
- `settings_reset-nice_nano_v2-zmk.uf2`

Latest downloaded artifacts on your machine:

- `/home/finn/Downloads/sofle-zmk-b59d7f6/firmware/sofle_left-nice_nano_v2-zmk.uf2`
- `/home/finn/Downloads/sofle-zmk-b59d7f6/firmware/sofle_right-nice_nano_v2-zmk.uf2`
- `/home/finn/Downloads/sofle-zmk-b59d7f6/firmware/settings_reset-nice_nano_v2-zmk.uf2`

## Normal flash flow

1. Put **left** half in bootloader mode (double-tap reset).
2. A USB drive like `NICENANO`/`RPI-RP2` appears.
3. Copy `sofle_left-nice_nano_v2-zmk.uf2` to that drive.
4. Wait for auto-reboot and drive disconnect.
5. Repeat for **right** half with `sofle_right-nice_nano_v2-zmk.uf2`.
6. Power-cycle both halves and reconnect Bluetooth.

## Clean reset flow (when pairings are broken)

Use this when halves do not talk to each other, BLE is stuck, or host pairing is broken.

1. Flash `settings_reset-nice_nano_v2-zmk.uf2` to **left**.
2. Flash `settings_reset-nice_nano_v2-zmk.uf2` to **right**.
3. Flash normal firmware again:
  - left: `sofle_left-nice_nano_v2-zmk.uf2`
  - right: `sofle_right-nice_nano_v2-zmk.uf2`
4. Remove old Bluetooth pairing on host devices.
5. Re-pair keyboard from scratch.

## Troubleshooting

- If no USB drive appears, double-tap reset again.
- If copy fails, unplug/replug USB and retry bootloader mode.
- If only one half types, reflash both halves and run clean reset flow.
- If layout seems old, confirm you flashed the correct left/right UF2 files.