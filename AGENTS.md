# Repository Guidelines

This repository contains a custom OpenCode TUI theme based on Visual Studio Code's built-in **Dark 2026** and **Light 2026** themes.

## Project Layout

- `vs-code-2026.json` is the theme file users install into their OpenCode themes directory.
- `README.md` documents installation and usage.
- `LICENSE` contains the repository license.

Do not add generated files, local OpenCode config, screenshots, or tool caches unless they are intentionally part of the repository.

## Theme Format

The theme must stay compatible with OpenCode TUI custom themes:

- Use `$schema: "https://opencode.ai/theme.json"`.
- Keep reusable color aliases in `defs`.
- Keep resolved OpenCode tokens in `theme`.
- Prefer `{ "dark": "...", "light": "..." }` values for UI tokens so the theme works in both schemes.
- The theme id is the filename without extension: `vs-code-2026`.

OpenCode loads user themes from:

- macOS/Linux: `~/.config/opencode/themes/*.json`
- Windows: `%USERPROFILE%\.config\opencode\themes\*.json`

Do not require a plugin, `api.theme.install`, or `api.theme.set` for this theme. Do not tell users to hardcode the theme in `tui.json` unless they explicitly want it forced.

## Color Sources

The source palettes are VS Code's built-in themes:

- `2026 Dark`
- `2026 Light`

When updating colors, preserve the intent of those themes rather than inventing a new palette. If a direct OpenCode token equivalent does not exist, choose the closest VS Code semantic color and document any notable compromise in the PR or commit message.

## Contrast Rules

Maintain readable contrast in both schemes, especially for:

- selected list rows
- command palette rows
- status/error/warning/success text
- markdown code and code blocks
- diff added/removed lines

Important existing decision: `selectedListItemText.light` should be `#FFFFFF` because selected rows in light mode use a blue background. Do not change it back to dark text unless the selected background is changed too.

As a rule of thumb, aim for WCAG AA contrast for normal text where practical. OpenCode terminal rendering may differ by terminal, so visual checks still matter.

## Validation

Before considering changes complete, run at least:

```sh
python -m json.tool vs-code-2026.json > /dev/null
```

On Windows PowerShell, this is also acceptable:

```powershell
Get-Content -Raw .\vs-code-2026.json | ConvertFrom-Json | Out-Null
```

If OpenCode is available locally, smoke-test the theme by copying or symlinking `vs-code-2026.json` into the OpenCode themes directory, launching OpenCode, and selecting `vs-code-2026` via `/theme`.

Manual visual checks should cover:

- dark mode home screen
- light mode home screen
- `/theme` or command palette selection rows
- markdown/code rendering in a chat response
- diff display if possible

## Editing Rules

- Keep the JSON readable and grouped by purpose: `defs` first, `theme` second.
- Avoid unrelated formatting churn.
- Do not remove dark/light variants just because one mode was tested.
- Do not introduce build tooling unless there is a clear maintenance benefit.
- Update `README.md` whenever installation, theme id, file name, or screenshot paths change.

## Release Checklist

Before publishing or pushing a change:

1. Validate `vs-code-2026.json` parses as JSON.
2. Confirm the filename is still `vs-code-2026.json` unless intentionally changing the theme id.
3. Confirm `README.md` installation commands still point to the raw `vs-code-2026.json` file.
4. Confirm no local OpenCode config or machine-specific paths were committed.
5. If colors changed, visually test both dark and light schemes.
