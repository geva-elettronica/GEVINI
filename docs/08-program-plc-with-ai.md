# 8 · How to Program a PLC with Artificial Intelligence in 2026

> From the GEVA Elettronica blog — **[read the original article](https://shop.gevaelettronica.it/en/blog/post/2-how-to-program-a-plc-with-artificial-intelligence-in-2026)**
> (posted 06/20/2026, by Giorgio Evangelista).

For decades, PLC programming was a task reserved for highly specialized automation engineers.
Today, Artificial Intelligence is changing the way industrial software and automation systems are
developed.

Tools such as ChatGPT, Claude Code, and GitHub Copilot can generate code, suggest solutions, and
dramatically reduce development time.

But can a PLC really be programmed using AI?

The answer is yes—provided that the platform is open and flexible enough to take advantage of
modern development tools.

---

## The limitations of traditional PLCs

Many industrial PLCs rely on proprietary software environments and specialized programming
languages.

While this approach offers reliability and standardization, it also comes with several drawbacks:

- Expensive software licenses
- Steep learning curves
- Vendor lock-in
- Limited integration with modern AI development tools

In most cases, AI assistants cannot directly understand proprietary PLC projects or work
effectively within closed development environments.

---

## Why Arduino and AI work so well together

The Arduino ecosystem is one of the most documented development platforms in the world.

Millions of examples, libraries, tutorials, and public projects provide AI models with a vast
knowledge base, allowing them to generate code that is often immediately usable.

This makes Arduino-compatible industrial controllers, such as GEVINO PLCs, particularly suitable
for AI-assisted development.

For example, you can ask an AI assistant:

- Read data from a Modbus sensor every minute
- Send a GSM alarm when a digital input changes state
- Display temperature and humidity on a TFT screen
- Control a motor using an encoder
- Log machine data to an SD card

The AI can generate a first working version of the software within seconds.

---

## Claude Code: a new way to develop industrial software

Claude Code is one of the most interesting tools currently available for embedded and industrial
development.

Unlike traditional code assistants that generate only small snippets, Claude Code can analyze
entire projects, modify existing files, create new modules, and assist with software maintenance.

In a GEVINO project, Claude Code can:

- Create new application features
- Fix bugs and errors
- Add support for industrial protocols
- Generate technical documentation
- Refactor and optimize existing code

This can significantly reduce development time and increase productivity.

---

## Can you build automation systems without being a programmer?

Artificial Intelligence does not eliminate the need for technical knowledge.

However, it allows engineers, technicians, and system integrators to develop automation solutions
much faster than before.

In many cases, understanding the machine or process becomes more important than memorizing
programming syntax.

The ability to clearly describe the desired behavior is often enough for AI tools to generate a
solid starting point.

---

## A practical example

Imagine you need to control a water pump.

Instead of writing the entire program manually, you can simply describe the required behavior:

> "Turn on the pump when the tank level drops below 20%. Turn it off when the level exceeds 80%.
> Send an SMS alarm if the sensor stops responding."

An AI assistant can generate the control logic, recommend the required libraries, and provide a
functional code framework in seconds.

---

## GEVINO and Artificial Intelligence

GEVINO PLCs are designed to take advantage of the Arduino ecosystem and modern AI development
tools.

They support:

- Arduino IDE
- Visual Studio Code
- Claude Code
- GitHub Copilot
- ChatGPT

Powered by the ARM Cortex-M0+ SAMD21 processor and compatible with Arduino Zero, GEVINO
controllers provide a powerful and flexible platform for industrial automation, IoT applications,
machine control, and custom embedded systems.

---

## Conclusion

Artificial Intelligence is not replacing automation engineers. Instead, it is becoming one of the
most powerful tools available for accelerating software development.

Open platforms such as GEVINO enable developers and industrial companies to fully benefit from
AI-assisted programming, reducing development costs, shortening project timelines, and making
industrial automation more accessible.

The future of PLC programming is not about writing every line of code manually—it is about
collaborating with Artificial Intelligence to transform ideas into working automation systems
faster than ever before.

---

### Next steps

- Try it yourself → **[4 · Install the Claude app and generate your first example](04-install-claude-code.md)**
- Or with VS Code → **[6 · Install VS Code + Arduino Maker Workshop + Claude](06-install-vscode-claude-arduino.md)**
- Read why Arduino holds up in industrial settings → **[9 · Arduino Is Not Industrial? Let's Clear Up the Misconceptions](09-arduino-is-not-industrial.md)**
