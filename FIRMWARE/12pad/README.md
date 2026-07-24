# 12pad (STM32F401 Blackpill)

12-key macropad + 1 rotary encoder. QMK + VIA.

* Keyboard Maintainer: [juarendra ramadhani](https://github.com/juarendra)
* Hardware Supported: WeAct Blackpill STM32F401 (USB Type-C)
* Hardware Availability: [Positron Elektronik](https://github.com/juarendra/12pad-QMK-VIA)

## Build

Copy this folder to `qmk_firmware/keyboards/12pad`, then:

```sh
qmk compile -kb 12pad -km default
```

Result: `12pad_default.bin`

## Enter Bootloader (DFU)

Three ways:

* **Bootmagic**: hold the top-left key (encoder knob) while plugging in the USB cable
* **Physical**: hold the `BOOT0` button on the Blackpill, tap `NRST` (or plug in USB), then release `BOOT0`
* **Keycode**: press the `QK_BOOT` key if mapped in VIA

## Flash

With [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases): open the `.bin`, enter bootloader, click Flash.

Or via CLI:

```sh
qmk flash -kb 12pad -km default
```

Or with `dfu-util` directly:

```sh
dfu-util -a 0 -d 0483:df11 -s 0x08000000:leave -D 12pad_default.bin
```

## VIA

Device is auto-detected by [VIA](https://usevia.app/). For manual sideload use
[`12pad_via_definitions.json`](../../12pad_via_definitions.json) via the Design tab.
