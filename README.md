# VS Code 2026 Theme for OpenCode

OpenCode TUI theme based on the built-in **Dark 2026** and **Light 2026** themes from Visual Studio Code.

## Screenshots

<!-- Add screenshots here -->

### Dark

<img width="1283" height="808" alt="image" src="https://github.com/user-attachments/assets/840186f0-a3da-49fa-a508-611e337be1ef" />

### Light

<img width="1277" height="808" alt="image" src="https://github.com/user-attachments/assets/768839a1-6d87-4f62-9754-c88d582a7d28" />

## Installation

Download the theme JSON into your OpenCode themes directory.

### macOS / Linux

```sh
mkdir -p ~/.config/opencode/themes
curl -L \
  https://raw.githubusercontent.com/MRGRD56/opencode-vs-code-2026-theme/refs/heads/main/vs-code-2026.json \
  -o ~/.config/opencode/themes/vs-code-2026.json
```

### Windows (PowerShell)

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.config\opencode\themes" | Out-Null

Invoke-WebRequest `
  -Uri "https://raw.githubusercontent.com/MRGRD56/opencode-vs-code-2026-theme/refs/heads/main/vs-code-2026.json" `
  -OutFile "$env:USERPROFILE\.config\opencode\themes\vs-code-2026.json"
```

## Usage

Open OpenCode and select the theme with:

```text
/theme
```

Choose:

```text
vs-code-2026
```

Alternatively, set it explicitly in `~/.config/opencode/tui.json`:

```json
{
  "$schema": "https://opencode.ai/tui.json",
  "theme": "vs-code-2026"
}
```

If you want to freely switch themes from OpenCode and keep your last choice, do not hardcode `"theme"` in `tui.json`; just install the theme file and select it with `/theme`.

## Theme File

The theme is a single OpenCode theme JSON file:

```text
vs-code-2026.json
```

It includes both dark and light color variants mapped from VS Code's **Dark 2026** and **Light 2026** themes.
