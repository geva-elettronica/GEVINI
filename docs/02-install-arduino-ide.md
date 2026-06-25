# 2 · Install the Arduino IDE v2 and the SAMD21 compiler

Every **GEVINO** board is **Arduino Zero compatible**, so the simplest way to program it is the
official **Arduino IDE 2**, which ships an easy Board Manager for installing the **Arduino SAMD
core** — the compiler/toolchain for the Microchip **SAMD21** (32-bit ARM Cortex-M0+) that powers
every GEVINO.

This is the first step of the **Arduino IDE path**. Once it is done you will install the GEVINO
libraries and flash your first sketch (**[3 · Libraries + first example](03-install-libraries-first-sketch.md)**).

> **Time needed:** ~10 minutes. **You need:** a Windows 10/11 PC, an internet connection, and a USB
> cable for the GEVINO (a *data* cable, not charge-only).
>
> Prefer an all-in-one editor with AI built in? Skip this path and use
> **[6 · VS Code + Arduino Maker Workshop + Claude](06-install-vscode-claude-arduino.md)** instead.

---

## Overview of the steps

1. Download and install the **Arduino IDE 2**.
2. Install the **Arduino SAMD Boards** core (the SAMD21 compiler) from the Board Manager.
3. Connect the GEVINO and select **Arduino Zero (Native USB Port)** + its COM port.

---

## Step 1 — Install the Arduino IDE 2

1. Go to **https://www.arduino.cc/en/software** and download **Arduino IDE 2.x** for Windows
   (the *Installer* is the easiest option).
2. Run the installer and accept the defaults. Let it install the **Arduino USB drivers** if Windows
   asks — they are what makes the board appear as a COM port.
3. Launch the Arduino IDE.

---

## Step 2 — Install the SAMD core (the SAMD21 compiler)

The GEVINO is programmed through the official **Arduino SAMD Boards** core, which installs the
ARM Cortex-M0+ compiler and the Arduino Zero definitions.

1. Open **Tools → Board → Boards Manager…** (or click the boards icon in the left toolbar).
2. In the search box type **`SAMD`**.
3. Find **"Arduino SAMD Boards (32-bits ARM Cortex-M0+)"** and click **Install**.
4. Wait for the download to finish — it pulls the compiler and tools, so it can take a few minutes.

> The core installs under
> `C:\Users\<you>\AppData\Local\Arduino15\packages\arduino\hardware\samd\<version>\`.
> Remember this path — the **[SD-card bootloader configuration](05-sd-bootloader.md)** copies two
> files into it.

---

## Step 3 — Connect the board and select it

1. Plug the GEVINO into the PC with the USB cable.
2. In **Tools → Board → Arduino SAMD Boards**, choose **Arduino Zero (Native USB Port)**.
3. In **Tools → Port**, select the **COM port** that appeared for the board.

> **Driver note:** on the *Native USB Port* the GEVINO enumerates as an Arduino Zero. If Windows
> does not assign a COM port, double-tap the board's **reset** button to enter the bootloader and
> retry, or reinstall the Arduino USB drivers.

---

## Verify

| Check | How |
|-------|-----|
| IDE installed | The Arduino IDE 2 opens to an empty sketch. |
| SAMD core installed | **Arduino Zero** appears under Tools → Board → Arduino SAMD Boards. |
| Board detected | A **COM port** shows up in Tools → Port when the GEVINO is plugged in. |

A quick end-to-end test: open **File → Examples → 01.Basics → Blink**, press **Verify (✓)**. If it
compiles without errors, the SAMD21 compiler is correctly installed. (The on-board LED macros come
with the GEVINO library in the next step — for now, compiling Blink is enough to prove the toolchain.)

---

## Troubleshooting

- **No COM port / board not detected.** Use a data USB cable, try another port, and double-tap
  **reset** to force the bootloader. Reinstall the Arduino USB drivers if Windows still ignores it.
- **Boards Manager download fails.** Check the connection / proxy and retry; the core is large.
- **Compile error about C++ version.** GEVINO libraries need **C++17**, the default on recent SAMD
  cores — make sure the core is up to date.

---

### Next steps

- Install the board libraries and flash your first sketch → **[3 · Libraries + first example](03-install-libraries-first-sketch.md)**
- Not sure which board you have? → **[1 · Models overview](01-models-overview.md)**
