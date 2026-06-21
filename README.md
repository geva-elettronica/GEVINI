# GEVINO — User Manual

**GEVINO** is a family of affordable, Arduino-compatible **industrial / building-automation PLCs**
built around the Microchip **SAMD21** microcontroller (32-bit ARM Cortex-M0+). Every model is
**Arduino Zero compatible**, so you program it with the standard Arduino IDE / Arduino SAMD core
(and with VS Code, Cursor or OpenPLC).

Designed and manufactured by **[GEVA Elettronica](https://www.gevaelettronica.it)** (Italy).

This repository is the **shared manual** for the whole GEVINO family: which model to pick, how to
set up the programming environment, and how to open the enclosure safely. For the per-model
programming reference (pinout, macros, examples, `AGENTS.md`) see each board's own repository.

---

## The manual

| Document | What it covers |
|----------|----------------|
| **[1 · Models overview](docs/01-models-overview.md)** | The differences between the GEVINO models — pick the right board. |
| **[2 · Install VS Code + Claude Code + Arduino Maker Workshop](docs/02-install-vscode-claude-arduino.md)** | Set up the full programming toolchain on Windows from scratch. |
| **[3 · Open the enclosure without breaking it](docs/03-open-the-enclosure.md)** | How to open the case and reach the SD card without snapping the fragile hooks. |

---

## The models at a glance

| Model | Best for | Key I/O | Repository |
|-------|----------|---------|------------|
| **GEVINO Opto PNP** | Industrial automation | 11 opto inputs, 4 PNP outputs, 2 analog in | [GEVINO-Opto-PNP](https://github.com/gioreva/GEVINO-Opto-PNP) |
| **GEVINO Civile** | Home / building automation | 3–7 relays (5 A), 4×12 V inputs, M-Bus | [GEVINO-Civile](https://github.com/gioreva/GEVINO-Civile) |
| **GEVINO Motor** | Motor control | TB67S128 stepper/DC driver, 5 inputs, 4 PNP outputs | [GEVINO-Motor](https://github.com/gioreva/GEVINO-Motor) |
| **GEVINO TFT 7"/10"** | HMI / touch panel | 7"/10" capacitive touch, 12 inputs, 8 outputs | [GEVINO-TFT-7-10](https://github.com/gioreva/GEVINO-TFT-7-10) |

See **[Models overview](docs/01-models-overview.md)** for the full comparison.

---

## Common to every model

- 32-bit **ARM Cortex-M0+**, 48 MHz (Microchip SAMD21), **256 KB** Flash, **32 KB** RAM.
- **Arduino Zero compatible** — Arduino IDE / Arduino SAMD core, VS Code, Cursor, OpenPLC.
- **RS485** bus (half duplex) for connecting up to **255** GEVINO devices, M-Bus or other protocols.
- **micro-SD** card slot and a **USB** programming/debug port.
- Firmware update **over the Internet or from the SD card** via a dedicated bootloader.
- Optional **Ethernet, Wi-Fi, Bluetooth, RTC, cellular modem** and **CE certification**.

---

## Buy / contact

GEVINO PLCs are designed and produced by **GEVA Elettronica**.

- Website: https://www.gevaelettronica.it
- Shop: https://shop.gevaelettronica.it
- Email: email@gevaelettronica.it

## License

MIT — see [LICENSE](LICENSE).
