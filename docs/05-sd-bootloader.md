# 5 · Special configuration for GEVINO boards with the SD-card bootloader

GEVINO boards can be flashed **from the micro-SD card** through a dedicated bootloader — handy for
field/OTA updates where no PC is attached. This is **optional**: for normal programming over USB you
only need **Arduino Zero (Native USB Port)** (**[doc 2](02-install-arduino-ide.md)**) and nothing on
this page.

Enabling the SD bootloader means adding three GEVINO board entries to the Arduino IDE, by copying two
files from this repository's **[`Arduino IDE V2/`](../Arduino%20IDE%20V2/)** folder into the SAMD core.

> **You need:** the Arduino IDE 2 with the **SAMD core installed** (**[doc 2](02-install-arduino-ide.md)**),
> and the two files shipped here:
> [`Arduino IDE V2/boards.txt`](../Arduino%20IDE%20V2/boards.txt) and
> [`Arduino IDE V2/flash_with_SDbootloader.ld`](../Arduino%20IDE%20V2/flash_with_SDbootloader.ld).

---

## Step 1 — Find the SAMD core folder

The two files go into the installed SAMD core. Find its exact path:

1. In the Arduino IDE: **File → Preferences → Show verbose output during → compilation**.
2. Compile any sketch and read the path the compiler prints — it points at the core install, e.g.
   `C:\Users\<you>\AppData\Local\Arduino15\packages\arduino\hardware\samd\<version>\`
   (for example `…\samd\1.8.14\`).

---

## Step 2 — Copy the two files

Using the version folder you just found:

| Copy this file | Into this folder |
|----------------|------------------|
| [`boards.txt`](../Arduino%20IDE%20V2/boards.txt) | `…\packages\arduino\hardware\samd\<version>\` |
| [`flash_with_SDbootloader.ld`](../Arduino%20IDE%20V2/flash_with_SDbootloader.ld) | `…\packages\arduino\hardware\samd\<version>\variants\arduino_zero\linker_scripts\gcc\` |

> Back up the original `boards.txt` first if you want to keep the stock file. After copying, restart
> the Arduino IDE so it re-reads the boards.

---

## Step 3 — The three new board entries

Under **Tools → Board** you now have three GEVINO entries, each compiling the sketch from a different
flash start address:

| Board entry | Sketch starts at | Use it for |
|-------------|------------------|------------|
| **GEVINO SD bootloader** | `0x8000` | Building a `firmware.bin` to flash from the SD card (this page). |
| **GEVINO SAM-BA bootloader** | `0x2000` | The standard Arduino/SAM-BA USB bootloader. |
| **GEVINO no bootloader** | `0x0000` | A bare image with no bootloader (programmer/debugger flashing). |

---

## Step 4 — Build and flash from the SD card

1. Select **Tools → Board → GEVINO SD bootloader**.
2. Build the binary: **Sketch → Export Compiled Binary**. The `.bin` is written into the sketch
   folder (a `build` subfolder in newer IDE versions).
3. **Rename** that file to **`firmware.bin`** and copy it to a **FAT32-formatted** micro-SD card.
4. Insert the SD card and **power up** the GEVINO. If it finds `firmware.bin`, the **yellow LED**
   flashes, then blinks twice, and the new app launches.
5. **Delete `firmware.bin`** from the SD (or remove the card) afterwards — otherwise every power-up
   re-flashes the firmware.

---

## Verify

| Check | How |
|-------|-----|
| Entries added | **GEVINO SD bootloader**, **SAM-BA bootloader** and **no bootloader** appear under Tools → Board. |
| Binary built | `firmware.bin` exists after **Export Compiled Binary** (with the SD bootloader board selected). |
| Flash from SD | On power-up the yellow LED does the flash sequence and your app runs. |

---

## Troubleshooting

- **The three entries don't appear.** `boards.txt` was copied to the wrong version folder — recheck
  the verbose path from Step 1 and restart the IDE.
- **Compile/link error after switching boards.** `flash_with_SDbootloader.ld` is missing or in the
  wrong `linker_scripts/gcc` folder — re-copy it (Step 2).
- **The board re-flashes on every boot.** That's expected while `firmware.bin` is on the card —
  delete it or remove the SD once the update is done.
- **`boards.txt` rejected by a newer core.** If a future SAMD core version is incompatible with the
  shipped `boards.txt`, append only the three `GEVINO_*` board blocks (listed in
  [`Arduino IDE V2/Readme - Eng.txt`](../Arduino%20IDE%20V2/Readme%20-%20Eng.txt)) to the core's own
  `boards.txt` instead of replacing it.

---

### Next steps

- Back to programming over USB → **[3 · Libraries + first example](03-install-libraries-first-sketch.md)**
- Use the VS Code toolchain instead → **[6 · VS Code + Arduino Maker Workshop + Claude](06-install-vscode-claude-arduino.md)**
