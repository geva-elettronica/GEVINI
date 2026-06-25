# 4 · Install Claude Code and generate your first example

**Claude Code** is Anthropic's command-line AI coding assistant. Every GEVINO repository ships an
**`AGENTS.md`** file (the board's programming guide for AI assistants) and an **`llms.txt`** map of
the repo, so Claude can write correct firmware for your board — pin macros, the non-blocking coding
style, RS485/Modbus, Ethernet, SD and analog recipes.

This page installs Claude Code and uses it to generate a first sketch. It works alongside the
**[Arduino IDE path](02-install-arduino-ide.md)**: Claude writes the code, you compile/upload it with
the Arduino IDE.

> **Before you start:** have the **[board library installed](03-install-libraries-first-sketch.md)**
> and the board's repository folder on disk (cloned or unzipped) — Claude reads `AGENTS.md` from it.

---

## Step 1 — Install Node.js

Claude Code runs on **Node.js**.

1. Download the **LTS** installer from **https://nodejs.org/** and run it.
2. Accept the defaults; keep **"Add to PATH"** ticked.
3. Open a new terminal (PowerShell) and confirm it works:

   ```powershell
   node --version
   ```

---

## Step 2 — Install Claude Code

In the terminal, install it globally with npm:

```powershell
npm install -g @anthropic-ai/claude-code
```

Check the install:

```powershell
claude --version
```

> If `claude` is "not found", **close and reopen** the terminal so the updated PATH is loaded.

---

## Step 3 — Start Claude in your project and sign in

1. Change into your board's repository folder (the one with `AGENTS.md`):

   ```powershell
   cd path\to\GEVINO-Opto-PNP
   ```

2. Launch the assistant:

   ```powershell
   claude
   ```

3. The first run asks you to **sign in** (Claude account or Anthropic API key). Follow the link it
   prints, authorize, and you are ready.

---

## Step 4 — Generate your first example

Ask Claude to read the board guide first, then describe what you want. For example:

> *"Read AGENTS.md, then write a sketch that turns on Out1 when In1 is active and prints the analog
> inputs to the USB serial every second."*

Claude reads `AGENTS.md` / `llms.txt`, learns the board's pin macros and non-blocking style, and
writes the `.ino`. Then compile and upload it with the Arduino IDE (**[doc 3, Step 3](03-install-libraries-first-sketch.md)**)
— or, if you use the VS Code path, build it straight from the editor
(**[doc 6](06-install-vscode-claude-arduino.md)**).

> **Tip:** keep requests small and concrete ("add a 500 ms debounce on In3", "send the value over
> RS485"), and always ask Claude to follow the non-blocking method described in `AGENTS.md` — no
> `delay()` in `loop()`.

---

## Verify

| Check | How |
|-------|-----|
| Node.js works | `node --version` prints a version. |
| Claude Code works | `claude --version` prints a version; `claude` opens the assistant. |
| Board context loaded | Claude references the board's macros (e.g. `In1`, `setOut1`) after reading `AGENTS.md`. |

---

## Troubleshooting

- **`claude` not found after install.** Restart the terminal so the PATH refresh is picked up;
  confirm Node.js was installed with "Add to PATH".
- **Claude writes generic Arduino code.** Tell it explicitly to **read `AGENTS.md`** first and run it
  from inside the board's repository folder.
- **Sketch does not compile.** Paste the compiler error back to Claude and ask it to fix it; make
  sure the **board library is installed** (**[doc 3](03-install-libraries-first-sketch.md)**).

---

### Next steps

- Flash firmware from the SD card (field/OTA updates) → **[5 · SD-card bootloader](05-sd-bootloader.md)**
- Want Claude *inside* the editor, next to Verify/Upload buttons? → **[6 · VS Code + Arduino Maker Workshop + Claude](06-install-vscode-claude-arduino.md)**
