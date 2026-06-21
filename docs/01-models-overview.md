# 1 · GEVINO Models Overview

All GEVINO PLCs share the same brain — a Microchip **SAMD21** (32-bit ARM Cortex-M0+, 48 MHz,
256 KB Flash, 32 KB RAM), **Arduino Zero compatible** — and the same RS485 bus, micro-SD slot,
USB programming port and bootloader. What changes between models is the **I/O and the front end**:
relays vs. transistor outputs, a touch display, a motor driver, and so on.

Use this page to pick the right board. Each model links to its own repository, where you will find
the pinout, the support library, ready-to-flash examples and the `AGENTS.md` programming guide.

---

## Quick decision guide

| If you need to… | Choose |
|------------------|--------|
| Drive industrial loads with protected transistor outputs and opto-isolated sensors | **GEVINO Opto PNP** |
| Switch mains / 220 V loads with relays in a home or building | **GEVINO Civile** |
| Drive a stepper or brushed-DC motor with current control | **GEVINO Motor** |
| Build an operator panel / HMI with a touch screen | **GEVINO TFT 7"/10"** |

---

## Comparison table

| | **Opto PNP** | **Civile** | **Motor** | **TFT 7"/10"** |
|---|---|---|---|---|
| **Purpose** | Industrial PLC | Home / building automation | Motor control | HMI / touch panel |
| **Power supply** | 7–40 V | 12 V (opt. internal 220 VAC PSU) | 7–40 V | 12 / 24 V (opt. 220 VAC PSU) |
| **Digital inputs** | 11 opto-isolated, dual polarity | 4 × 12 V | 5 PNP | 12 opto-isolated (4 high-speed/IRQ) |
| **Digital outputs** | 4 PNP (40 V 2.5 A) + 2 NPN aux | 3 relays 5 A → up to 7 | 4 PNP (40 V 2.5 A) | 8 opto (PNP/NPN/AC, 1 A 30 V) |
| **Analog** | 2 inputs (12-bit) | — | 3 inputs + 2 motor-current | 4 inputs + 1 output (0–10 V / 4–20 mA) |
| **Display** | — | opt. OLED 128×128 | — | **7" or 10" capacitive touch, 1024×600** |
| **Motor driver** | — | — | **Toshiba TB67S128FTG** | opt. 27 V 43 A DC driver |
| **RS485** | ✓ | ✓ + M-Bus | ✓ | ✓ |
| **Storage / ports** | micro-SD, USB-C | micro-SD, micro-USB | micro-SD, USB-C | rear micro-SD + USB-C, **front USB stick** |
| **Repository** | [GEVINO-Opto-PNP](https://github.com/gioreva/GEVINO-Opto-PNP) | [GEVINO-Civile](https://github.com/gioreva/GEVINO-Civile) | [GEVINO-Motor](https://github.com/gioreva/GEVINO-Motor) | [GEVINO-TFT-7-10](https://github.com/gioreva/GEVINO-TFT-7-10) |

---

## GEVINO Opto PNP — the industrial workhorse

The general-purpose industrial PLC. Opto-isolated inputs and short-circuit-protected PNP outputs
make it robust against the electrical noise of a real machine.

- **11 opto-isolated inputs**, positive or negative common (dual polarity).
- **4 short-circuit-protected PNP outputs**, 40 V / 2.5 A — resistive, inductive and capacitive loads.
- **2 analog inputs**, 20 mA / 1 V / 10 V, 12-bit (optionally re-used as 2 NPN aux outputs via DIP switch).
- Protected against **inductive loads, ESD and EMI**.
- Optional Ethernet, Wi-Fi, Bluetooth, RTC, RS232, cellular modem and CE certification.

→ [Repository & programming guide](https://github.com/gioreva/GEVINO-Opto-PNP)

---

## GEVINO Civile — home & building automation

The model for civil installations: real **relays** that switch mains loads, 12 V inputs, and a rich
set of radios. It also accepts an internal 220 VAC power supply, so it runs straight off the mains.

- **3 relays** 250 VAC / 30 VDC, 5 A — expandable to **7 outputs** (K1…K7).
- **4 digital inputs**, 12 V.
- RS485 **+ M-Bus**; up to **5 serial ports** (USB, Wi-Fi, modem, RS485, M-Bus).
- **19 status LEDs**, I²C + SPI buses.
- Options: Ethernet, Wi-Fi, Bluetooth, RTC, SIM800 modem, M-Bus, internal 220 V PSU, OLED 128×128.

> Note: the 4 extra relays are available **only without the Ethernet module**. With Ethernet fitted,
> **one** extra relay can still be added via a 2-pin terminal.

→ [Repository & programming guide](https://github.com/gioreva/GEVINO-Civile)

---

## GEVINO Motor — stepper / DC motor control

The Opto PNP I/O set **plus** a powerful Toshiba motor driver with constant-current control and fine
microstepping, all driven over SPI from software.

- **Toshiba TB67S128FTG**: one **stepper** or two **brushed-DC** motors.
- Constant current **50 V / 5 A (10 A peak)** per phase.
- Microstepping: full, half, 1/4, 1/8, 1/16, 1/32, 1/64, **1/128**.
- Software control: torque, frequency limits, step selection, **current reading**, ADMD, anti-stall.
- **5 PNP inputs**, **4 protected PNP outputs**, **3 analog inputs** + 2 channels reading motor phase currents.

→ [Repository & programming guide](https://github.com/gioreva/GEVINO-Motor)

---

## GEVINO TFT 7"/10" — the touch HMI

A complete operator panel: a large capacitive-touch display on top of industrial I/O. The **7" and
10" models are the same board** — only the glass (panel + touch controller) changes, and the
firmware auto-detects which one is fitted.

- **7" or 10" capacitive-touch TFT**, 1024×600, 400 cd/m² (Raio **RA8876** controller).
- **12 opto-isolated inputs** (4 high-speed with interrupt), **8 opto outputs** (PNP/NPN/AC, 1 A 30 V).
- **4 analog inputs** + **1 analog output** (0–10 V or 4–20 mA).
- **Front USB** port to read/write a USB memory stick; rear micro-SD + USB-C.
- **DMA image loading**: a full 1024×600 color image in ~80 ms.
- Many options: DC-DC isolator, 220 V PSU, RTC, RS232, SIM800L (with audio), Wi-Fi, Bluetooth,
  Ethernet, LoRa, a 27 V 43 A DC motor driver, acrylic frame and rear cover.

→ [Repository & programming guide](https://github.com/gioreva/GEVINO-TFT-7-10)

---

## What every model has in common

- 32-bit **ARM Cortex-M0+**, 48 MHz (SAMD21), **256 KB** Flash, **32 KB** RAM.
- **Arduino Zero compatible** programming (Arduino IDE, VS Code, Cursor, OpenPLC).
- **RS485** half-duplex bus, up to **255** devices, M-Bus or other protocols.
- **micro-SD** card slot and a **USB** programming / debug port.
- Firmware update **over the Internet or from the SD card** via a dedicated bootloader.

---

### Next steps

- Set up the programming environment → **[2 · Install VS Code + Claude Code + Arduino Maker Workshop](02-install-vscode-claude-arduino.md)**
- Need to open the case to fit a module or inspect the board (GEVINO Opto)? → **[Opening of GEVINO Opto](https://github.com/geva-elettronica/GEVINO-Opto-PNP/blob/main/docs/open-the-enclosure.md)**
