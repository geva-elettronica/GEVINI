# 4 · Install the Claude app and generate your first example

**Claude** is Anthropic's AI assistant, available as a desktop app for Windows and Mac. The app
includes **Code**, a built-in coding mode (the same engine as Claude Code) that can read and write
files in a project folder on your PC. Every GEVINO repository ships an **`AGENTS.md`** file (the
board's programming guide for AI assistants) and an **`llms.txt`** map of the repo, so Claude can
write correct firmware for your board — pin macros, the non-blocking coding style, RS485/Modbus,
Ethernet, SD and analog recipes.

This page installs the Claude app and uses its **Code** mode to generate a first sketch. It works
alongside the **[Arduino IDE path](02-install-arduino-ide.md)**: Claude writes the code, you
compile/upload it with the Arduino IDE.

> **Before you start:** have the **[board library installed](03-install-libraries-first-sketch.md)**
> in your Arduino sketchbook folder — Claude reads the library's `AGENTS.md` from there.

---

## Step 1 — Install the Claude app

1. Go to **https://claude.ai/download** and download the installer for Windows.
2. Run the installer and accept the defaults.
3. Launch the **Claude** app when it finishes installing.

---

## Step 2 — Sign in

1. On first launch, sign in with your **Claude account** (create one if you don't have it yet).
2. Once signed in you land on the main Claude window, with **Chats** and **Code** in the side bar.

> **Subscription needed:** the **Code** mode is not available on the free plan. Subscribe to at
> least a **Pro** plan (billed monthly, cancel anytime) to unlock it and try it for a month.

---

## Step 3 — Open your Arduino folder in Code

1. In the side bar, click **Code**.
2. Start a new Code session and, when asked for a project folder, pick your **Arduino sketchbook
   folder** — not the library folder itself — typically:

   ```
   C:\Users\<you>\Documents\Arduino
   ```

   This is the same folder that already contains `libraries\` (with your board's library inside,
   e.g. `libraries\GEVINO-Opto-PNP\`) and is where new sketches should be created, so the Arduino
   IDE can find and open them right away.
3. Claude now works directly on the files in that folder, the same way the command-line Claude Code
   does — it can read the library's `AGENTS.md`/`llms.txt` and create a new sketch alongside your
   others.

---

## Step 4 — Generate your first example

Ask Claude to read the board guide first, then describe what you want, telling it where the guide
is relative to the Arduino folder you opened. For example:

> *"Leggi il file libraries/GEVINO-Opto-PNP/AGENTS.md e crea un programma che accenda Out1 quando
> In1 è attivo e stampi gli ingressi analogici sulla seriale USB ogni secondo."*

(swap in the library folder name for your board, e.g. `libraries/GEVINO-Civile/AGENTS.md`)

Claude reads `AGENTS.md` / `llms.txt`, learns the board's pin macros and non-blocking style, and
creates a new sketch folder with the `.ino` inside your Arduino sketchbook — so it shows up directly
under **File → Sketchbook** in the Arduino IDE. Then compile and upload it
(**[doc 3, Step 3](03-install-libraries-first-sketch.md)**) — or, if you use the VS Code path,
build it straight from the editor (**[doc 6](06-install-vscode-claude-arduino.md)**).

> **Tip:** keep requests small and concrete ("add a 500 ms debounce on In3", "send the value over
> RS485"), and always ask Claude to follow the non-blocking method described in `AGENTS.md` — no
> `delay()` in `loop()`.

---

## Verify

| Check | How |
|-------|-----|
| Claude app installed | The **Claude** app opens and you are signed in. |
| Code mode works | Clicking **Code** and picking your Arduino folder opens a working session on it. |
| Board context loaded | Claude references the board's macros (e.g. `In1`, `setOut1`) after reading the library's `AGENTS.md`. |
| Sketch shows up in the IDE | The new sketch appears under **File → Sketchbook** in the Arduino IDE, no copying needed. |

---

## Troubleshooting

- **Can't find "Code" in the app.** Make sure the app is up to date (check for updates from the
  app's menu) — Code mode ships in recent versions of the Claude desktop app.
- **Claude writes generic Arduino code.** Tell it explicitly to **read the library's `AGENTS.md`**
  first (e.g. `libraries/GEVINO-Opto-PNP/AGENTS.md`) and make sure the Code session's project folder
  is your Arduino sketchbook folder, with the board's library already installed under `libraries\`.
- **Sketch does not compile.** Paste the compiler error back to Claude and ask it to fix it; make
  sure the **board library is installed** (**[doc 3](03-install-libraries-first-sketch.md)**).

---

### Next steps

- Flash firmware from the SD card (field/OTA updates) → **[5 · SD-card bootloader](05-sd-bootloader.md)**
- Want Claude *inside* the editor, next to Verify/Upload buttons? → **[6 · VS Code + Arduino Maker Workshop + Claude](06-install-vscode-claude-arduino.md)**
