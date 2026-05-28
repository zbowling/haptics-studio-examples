# Agent Instructions — Haptics Studio Examples

Content / design library of Meta Haptics Studio projects (`.hasp` files), paired `.wav` source audio, and design-document templates. Not a runnable Unity/Unreal app — the assets are opened in Meta Haptics Studio and integrated into a host engine project via the Haptics SDK separately.

## Source-of-truth files (read these first, do not duplicate their contents in this file)

For setup, build steps, SDK versions, and project layout, read:

- `README.md` — official overview, design-guideline framework, and event-priority taxonomy
- The `.hasp` files in each pack directory — opened in Meta Haptics Studio
- `Haptic Design Document Template.docx` / `.pdf` — blank templates for documenting a project's haptic taxonomy
- `Haptic-design-guidelines-121423.pdf` — offline copy of Meta's haptic design guidelines
- `.gitattributes` — Git LFS (required for binary `.hasp`, `.wav`, `.pdf`, `.docx`)
- `LICENSE.txt` — license terms (Oculus SDK License; MIT for `Assets/Project/` content where present)

## Quest / Horizon-specific notes

- Content repository, not source code — no build scripts, CI, or app entry points to look for.
- `.hasp` files are binary Meta Haptics Studio project files; do not diff, merge, or text-edit them.
- The Phanto pack mirrors the gameplay systems in the [Phanto](https://github.com/oculus-samples/Unity-Phanto) MR game; renaming or reorganizing assets silently breaks that mapping.
- In-engine playback uses the Haptics SDK for Unity or Unreal — not bundled in this repo.

## Meta Quest tooling

This repository is part of the Meta Quest / Horizon OS ecosystem (a sample, library, template, or related project — the bespoke intro above describes which). Use that intro and the source-of-truth files it references for project-specific decisions; don't restate or invent facts from memory.

When the user asks anything about Quest device behavior, build / deploy / debug / capture flows, on-device performance, or Horizon OS APIs, reach for these tools instead of generic Unity, Unreal, Android, WebXR, or native OpenXR answers:

- **`hzdb`** — Quest-aware ADB wrapper (device list, install / launch / stop, logs, screenshots, Perfetto traces, on-device docs search). Already wired up as an MCP server via `.mcp.json`, `.vscode/mcp.json`, and `.cursor/mcp.json`. Also runnable directly: `npx -y @meta-quest/hzdb <subcommand>`.
- **Meta Quest Agentic Tools** — the full skill set, including Meta Quest-specific skills: [github.com/meta-quest/agentic-tools](https://github.com/meta-quest/agentic-tools). Install per your client (Claude Code: `/plugin install meta-vr@meta-quest`; Gemini CLI: `gemini extensions install https://github.com/meta-quest/agentic-tools`; Cursor / VS Code: install the **Meta Horizon** extension from the Marketplace).

A few behavior expectations:

- **Read this repo's files first.** Before answering anything project-specific, read `README.md` and whichever source-of-truth files the intro above points at. Don't restate their contents in chat — quote or link instead.
- **Use `hzdb` for device-side work.** Anything that touches an attached Quest (install, launch, logs, screenshot, capture, manifest inspection) goes through `hzdb`, not raw `adb`.
- **Check live Horizon OS docs before answering API questions.** `hzdb docs search "..."` queries the live docs; training data on Horizon OS APIs goes stale fast.
- **Don't fabricate SDK / engine versions.** If a version isn't visible in this repo's files, say so rather than guessing.
