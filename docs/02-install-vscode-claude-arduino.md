# 2 · Install VS Code + Claude Code + Arduino Maker Workshop

This guide sets up a complete environment to program any **GEVINO** board on **Windows**, using:

- **Visual Studio Code** — the editor.
- **Arduino Maker Workshop** — a VS Code extension that compiles and uploads Arduino sketches
  (it uses `arduino-cli` under the hood, so the classic Arduino IDE is **not** required).
- **Claude Code** — Anthropic's AI coding assistant, running inside the VS Code terminal. Each
  GEVINO repository ships an `AGENTS.md` file that teaches Claude how to write firmware for that board.

> **Time needed:** ~20 minutes. **You need:** a Windows 10/11 PC with administrator rights, an
> internet connection, and a USB cable for the GEVINO.

---

## Overview of the steps

1. Install **Visual Studio Code**.
2. Install the **Arduino Maker Workshop** extension (it installs `arduino-cli` for you).
3. Install the **Arduino SAMD core** and select the **Arduino Zero** board.
4. Install **Node.js**, then **Claude Code**.
5. Open a GEVINO repository and start programming.

---

## Step 1 — Install Visual Studio Code

1. Download VS Code from **https://code.visualstudio.com/** and run the installer.
2. On the *Select Additional Tasks* screen, tick **"Add to PATH"** and (optionally)
   **"Add 'Open with Code' action"** — they make the next steps easier.
3. Launch VS Code when the installer finishes.

---

## Step 2 — Install the Arduino Maker Workshop extension

1. In VS Code, open the **Extensions** view: click the squares icon in the left bar, or press
   `Ctrl+Shift+X`.
2. Search for **`Arduino Maker Workshop`** (publisher *thien.io* / "Arduino Maker Workshop").
3. Click **Install**.
4. The first time it runs, the extension offers to **download and install `arduino-cli`**
   automatically — accept. Wait until the status bar at the bottom shows it is ready.

> Arduino Maker Workshop is a self-contained alternative to the old "vscode-arduino" extension:
> it bundles its own `arduino-cli`, so you do **not** need to install the standalone Arduino IDE.

---

## Step 3 — Install the SAMD core and select the board

GEVINO is **Arduino Zero compatible**, so it uses the official **Arduino SAMD Boards** core.

1. Open the Command Palette (`Ctrl+Shift+P`) and run **"Arduino Maker Workshop: Board Manager"**
   (or use the Boards panel the extension adds to the side bar).
2. Search for **"Arduino SAMD Boards (32-bits ARM Cortex-M0+)"** and **install** it.
3. Set the board to **Arduino Zero (Native USB Port)**:
   - Connect the GEVINO with the USB cable.
   - In the extension's board selector, choose **Arduino Zero (Native USB Port)**.
   - Select the **COM port** that appears for the board.

> **Driver note:** on the *Native USB Port* the GEVINO enumerates as an Arduino Zero. If Windows
> does not assign a COM port, install the Arduino USB drivers (bundled with the Arduino IDE) once,
> or double-tap the board's **reset** button to enter the bootloader and retry.

### Optional — SD-card bootloader (GEVINO-specific)

GEVINO boards can also be flashed **from the micro-SD card** using a dedicated bootloader. This
requires copying GEVINO's `boards.txt` and `flash_with_SDbootloader.ld` into the SAMD core folder
(typically `…\Arduino15\packages\arduino\hardware\samd\<version>\`). This is **optional** and only
needed for SD/OTA updates — see the *Arduino IDE V2* notes shipped by GEVA. For normal USB
programming you do **not** need it.

---

## Step 4 — Install Claude Code

Claude Code is a command-line AI assistant that runs in the integrated terminal.

1. **Install Node.js (LTS)** from **https://nodejs.org/** — Claude Code needs it. Accept the
   defaults; make sure *"Add to PATH"* stays ticked.
2. Restart VS Code so it picks up Node in the PATH.
3. Open a terminal in VS Code: menu **Terminal → New Terminal** (`` Ctrl+` ``).
4. Install Claude Code globally:

   ```powershell
   npm install -g @anthropic-ai/claude-code
   ```

5. (Recommended) Install the **Claude Code for VS Code** extension from the Extensions view — it
   adds an inline panel and shows file diffs as Claude edits them.
6. Start Claude Code from the terminal, inside your project folder:

   ```powershell
   claude
   ```

   The first run asks you to **sign in** (Claude account or Anthropic API key). Follow the link it
   prints, authorize, and you are ready.

---

## Step 5 — Open a GEVINO project and start

1. **Get a GEVINO repository.** Either clone it with git, or download the ZIP from GitHub and unzip:

   ```powershell
   git clone https://github.com/gioreva/GEVINO-Opto-PNP.git
   ```

   (Swap in `GEVINO-Civile`, `GEVINO-Motor` or `GEVINO-TFT-7-10` for the other models.)
2. In VS Code: **File → Open Folder…** and pick the repository folder.
3. Open one of the sketches in `examples/` (e.g. the board test). Use Arduino Maker Workshop's
   **Verify/Compile** and **Upload** buttons (in the status bar / side panel) to build and flash it.
4. Start Claude Code in the VS Code terminal:

   ```powershell
   claude
   ```

   Then just describe what you want, for example:

   > *"Read AGENTS.md, then write a sketch that turns on Out1 when In1 is active."*

   Each GEVINO repo includes an **`AGENTS.md`** (the board's programming guide for AI assistants)
   and an **`llms.txt`** map of the repository — Claude reads them to learn the board's pin macros,
   the non-blocking coding style, RS485/Modbus, Ethernet, SD and analog recipes.

---

## Verify the toolchain

| Check | How |
|-------|-----|
| `arduino-cli` works | Arduino Maker Workshop status bar shows a board + port, with no error toast. |
| SAMD core installed | The board list contains **Arduino Zero**. |
| Board detected | A **COM port** appears when the GEVINO is plugged in. |
| Node.js works | `node --version` prints a version in the terminal. |
| Claude Code works | `claude --version` prints a version; `claude` opens the assistant. |

---

## Troubleshooting

- **No COM port / board not detected.** Try a different USB cable (a data cable, not charge-only),
  a different port, and double-tap **reset** to force the bootloader. Install the Arduino USB
  drivers if Windows still ignores the board.
- **Upload fails / "port busy".** Close any other serial monitor holding the port, then retry.
- **`claude` not found after install.** Restart the terminal (or VS Code) so the updated PATH is
  loaded; confirm Node.js was installed with "Add to PATH".
- **Compile error about C++ version.** GEVINO libraries need **C++17**, which is the default on
  recent Arduino SAMD cores — make sure the SAMD core is up to date.

---

### Next steps

- Not sure which board you have? → **[1 · Models overview](01-models-overview.md)**
- Need to open the case for an internal modification (GEVINO Opto)? → **[Opening of GEVINO Opto](https://github.com/geva-elettronica/GEVINO-Opto-PNP/blob/main/docs/open-the-enclosure.md)**
