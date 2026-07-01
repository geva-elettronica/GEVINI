# GEVINO — User Manual

**GEVINO** is a family of affordable, Arduino-compatible **PLCs for industry and home automation**,
built around the Microchip **SAMD21** microcontroller (32-bit ARM Cortex-M0+). Every model is
**Arduino Zero compatible**, so you program it with the standard Arduino IDE / Arduino SAMD core
(and with VS Code, Cursor or OpenPLC).

Designed and manufactured by **[GEVA Elettronica](https://www.gevaelettronica.it)** (Italy).

This repository is the **shared manual** for the whole GEVINO family: which model to pick and how to
set up the programming environment. For the per-model programming reference (pinout, macros,
examples, `AGENTS.md`) and hardware guides see each board's own repository.

---

## The manual

**Start here → [1 · Models overview](docs/01-models-overview.md)** — compare the GEVINO models and
pick the right board.

Then set up the programming toolchain. There are **two routes — pick one, you don't need both:**

### 🅐 Arduino IDE — the classic route

1. **[Install the Arduino IDE v2 + SAMD21 compiler](docs/02-install-arduino-ide.md)**
2. **[Install the libraries + compile the first example](docs/03-install-libraries-first-sketch.md)**
3. **[Install Claude Code + generate a first example](docs/04-install-claude-code.md)**
4. **[SD-card bootloader](docs/05-sd-bootloader.md)** — *optional, only for SD/OTA field updates*

### 🅑 VS Code — the all-in-one route

- **[Install VS Code + Arduino Maker Workshop + Claude](docs/06-install-vscode-claude-arduino.md)** —
  editor, compiler and AI assistant in a single window. *(The SD-card bootloader, step 4 above,
  applies here too.)*

---

## The models at a glance

| Model | Best for | Key I/O | Repository |
|-------|----------|---------|------------|
| **GEVINO Opto PNP** | Industrial automation | 11 opto inputs, 4 PNP outputs, 2 analog in | [GEVINO-Opto-PNP](https://github.com/geva-elettronica/GEVINO-Opto-PNP) |
| **GEVINO Civile** | Home / building automation | 3–7 relays (5 A), 4×12 V inputs, M-Bus | [GEVINO-Civile](https://github.com/geva-elettronica/GEVINO-Civile) |
| **GEVINO Motor** | Motor control | TB67S128 stepper/DC driver, 5 inputs, 4 PNP outputs | [GEVINO-Motor](https://github.com/geva-elettronica/GEVINO-Motor) |
| **GEVINO TFT 7"/10"** | HMI / touch panel | 7"/10" capacitive touch, 12 inputs, 8 outputs | [GEVINO-TFT-7-10](https://github.com/geva-elettronica/GEVINO-TFT-7-10) |

See **[Models overview](docs/01-models-overview.md)** for the full comparison.

---

## From the blog

- **[7 · Why Choose GEVINO Instead of a Traditional PLC?](docs/07-why-choose-gevino-vs-plc.md)**
- **[8 · How to Program a PLC with Artificial Intelligence in 2026](docs/08-program-plc-with-ai.md)**
- **[9 · Arduino Is Not Industrial? Let's Clear Up the Misconceptions](docs/09-arduino-is-not-industrial.md)**

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
