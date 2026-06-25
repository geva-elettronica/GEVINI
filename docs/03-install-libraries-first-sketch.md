# 3 · Install the GitHub libraries and compile your first example

Each GEVINO model has its **own GitHub repository** that is also an **Arduino library**: a
single-header support library (the board's pin macros and helpers) plus ready-to-flash **examples**.
This page installs that library into the Arduino IDE and compiles/uploads the first example.

> **Before you start:** finish **[2 · Install the Arduino IDE v2 and the SAMD21 compiler](02-install-arduino-ide.md)**
> — you need the SAMD core installed and the board selected as **Arduino Zero (Native USB Port)**.

---

## Step 1 — Get your board's repository

Pick the repository that matches your board:

| Model | Repository |
|-------|------------|
| GEVINO Opto PNP | https://github.com/geva-elettronica/GEVINO-Opto-PNP |
| GEVINO Civile | https://github.com/geva-elettronica/GEVINO-Civile |
| GEVINO Motor | https://github.com/geva-elettronica/GEVINO-Motor |
| GEVINO TFT 7"/10" | https://github.com/geva-elettronica/GEVINO-TFT-7-10 |

Download it in either of two ways:

- **ZIP (simplest):** on the repository page click **Code → Download ZIP**.
- **git:** `git clone https://github.com/geva-elettronica/GEVINO-Opto-PNP.git`
  (swap in the repository for your board).

---

## Step 2 — Add the library to the Arduino IDE

**If you downloaded the ZIP:**

1. In the Arduino IDE: **Sketch → Include Library → Add .ZIP Library…**
2. Select the downloaded `.zip`.

**If you cloned with git:** copy (or move) the repository folder into your Arduino libraries folder,
typically `C:\Users\<you>\Documents\Arduino\libraries\`.

Either way, the board's examples now appear under **File → Examples → GEVINO**.

> The library is **self-contained** (no external dependencies) and needs **C++17**, which is the
> default on recent SAMD cores.

---

## Step 3 — Open and compile the first example

1. Open **File → Examples → GEVINO** and pick a starter sketch — the **board test** example is a
   good first one (e.g. `GEVINO_opto_PNP_Test` for the Opto PNP; each repo lists its examples in
   the README).
2. Make sure **Arduino Zero (Native USB Port)** and the right **COM port** are still selected
   (Tools menu).
3. Click **Verify (✓)** to compile.
4. Click **Upload (→)** to flash it to the GEVINO.

A minimal sketch looks the same on every model — include the one header, call the setup once, then
write non-blocking logic:

```cpp
#include "gevino_opto_pnp_io.h"   // the only include you need (header name varies per board)

void setup() {
  SerialUSB.begin(115200);        // USB debug console
  gevino_io_setup();              // configures ALL board I/O (do not init pins yourself)
}

void loop() {
  if (In1) setOut1;               // mirror input 1 onto output 1
  else     resOut1;
}
```

> Open the **Serial Monitor** (115200 baud) to see the debug output the test sketch prints.

---

## Verify

| Check | How |
|-------|-----|
| Library installed | The board appears under **File → Examples → GEVINO**. |
| Sketch compiles | **Verify** finishes with "Done compiling" and no red errors. |
| Upload works | **Upload** ends with "Done uploading"; the board's LEDs react / Serial Monitor prints. |

---

## Troubleshooting

- **`No such file` on the include.** The library is not installed — re-do Step 2, then restart the
  IDE so Examples refresh.
- **Upload fails / "port busy".** Close any open Serial Monitor holding the port, then retry. If the
  board is unresponsive, double-tap **reset** to force the bootloader and upload again.
- **`'In1' was not declared`.** You are compiling a sketch for a different board, or the wrong
  library is installed — match the example to your model.
- **C++17 errors.** Update the Arduino SAMD core (see **[doc 2](02-install-arduino-ide.md)**).

---

### Next steps

- Let an AI assistant write sketches for your board → **[4 · Install Claude Code + first example](04-install-claude-code.md)**
- Flash firmware from the SD card (OTA/field updates) → **[5 · SD-card bootloader](05-sd-bootloader.md)**
