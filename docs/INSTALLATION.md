# Installation

Two steps on either platform: extract, then double-click. The installer handles the parts
that usually go wrong.

---

## Before you start

**Vencord must be installed and run at least once.** Get it from
[vencord.dev/download](https://vencord.dev/download). Running it once creates the folder
the installer writes to. If that folder does not exist, the installer stops and says so.

**Discord must be in dark mode.** Settings → Appearance → Dark. The theme is dark-only.

---

## Windows

1. **Extract the zip first.** Right-click → *Extract All*.

   Do not run anything from inside Explorer's zip preview. That copies one file to a temp
   folder without its siblings and installs into a directory Windows later deletes. The
   installer detects this and refuses, but extracting takes two seconds.

2. **Double-click `INSTALL-WINDOWS.cmd`.**

3. **Pick a colour**, or just press Enter for violet. All six are in the package; this
   installs the one you choose. You can run it again later to switch.

That is the whole procedure.

If Discord is running, the installer offers to close it and reopen it for you — answer
`Y`. Reopening matters: window transparency is a startup flag, so a client that was only
reloaded shows a half-applied theme.

The window stays open at the end. If something went wrong, the reason is printed there.

<details>
<summary><strong>Why a .cmd and not the .ps1 directly?</strong></summary>

Because a zip that arrived over Discord, email or a browser is marked as untrusted by
Windows, and PowerShell then refuses the script **even with `-ExecutionPolicy Bypass`**.
The `.ps1` cannot clear that mark for itself, because Windows will not run it until the
mark is cleared. The `.cmd` is not subject to the same restriction, so it clears the mark
first and then launches the installer.

It also keeps the window open. "Run with PowerShell" closes it the instant the script
ends — including when it ends with an error, which is why the usual symptom is a window
that flashes for a second and appears to do nothing.

</details>

<details>
<summary><strong>Driving it manually</strong></summary>

```powershell
.\install-windows.ps1 -DryRun     # show the plan, write nothing
.\install-windows.ps1
```

If Windows blocks the script:

```powershell
Get-ChildItem -Recurse | Unblock-File
```

</details>

---

## macOS

1. Extract the zip.
2. Double-click `install-macos.command`, pick a colour (Enter for violet), or from a
   terminal:

```bash
./install-macos.command --dry-run     # show the plan, write nothing
./install-macos.command
```

> **Honest status:** the theme is confirmed working on macOS. The installer's **first real
> Mac run failed** — on packaging, not on logic. The zip carried no executable bit (Finder
> said "you do not have permission") and the script had Windows line endings (a `sudo`
> attempt then failed on the shebang). Both are fixed in the current build, which refuses
> to produce a zip that has either problem. **The fixed installer has not yet been re-run
> on a Mac.** Run `--dry-run` first; if you are the one who confirms it, that closes the
> last real gap in the package.
>
> If a copy you received still fails with "no permission", the workaround is one line in
> Terminal from the extracted folder — `chmod +x install-macos.command` — and then run it.
> If it then fails on the shebang, you have an old zip; ask for the rebuilt one.

---

## Options

| macOS | Windows | Effect |
|---|---|---|
| `--colour <name>` | `-Colour <name>` | `violet` (default), `blurple`, `matrix`, `space`, `blood`, `bee`. Skips the prompt |
| `--dry-run` | `-DryRun` | Print the plan, write nothing |
| `--no-transparency` | `-NoTransparency` | Skip the transparent-window flag |
| `--no-plugin-settings` | `-NoPluginSettings` | Enable the plugins, keep your own preferences |
| `--no-font` | `-NoFont` | Skip installing JetBrains Mono |
| `--prune-missing-themes` | `-PruneMissingThemes` | Drop `enabledThemes` entries whose `.css` is gone |
| `--force` | `-Force` | Install while Discord is running (not advised) |
| `--dir <path>` | `-Dir <path>` | Target one specific client folder |

---

## What it actually does

1. **Installs JetBrains Mono**, per-user — `%LOCALAPPDATA%\Microsoft\Windows\Fonts` plus
   the `HKCU` font key, or `~/Library/Fonts`. Never machine-wide, so no elevation prompt.
2. **Finds your client** — Vencord and Vesktop. Installs into every one it finds.
3. **Copies the theme** into `<client>/themes/`.
4. **Backs up `settings.json`** to `settings.json.bak-omni-<timestamp>`.
5. **Merges** into `settings.json` — never replaces. Enables the 52 plugins with their
   preferences, adds the theme to `enabledThemes` keeping anything already there, and sets
   `transparent: true`.
6. **Re-parses the result before writing**, then writes atomically via a temp file and
   rename, so a crash mid-write cannot leave a half-written config.

Anything not listed in the profile is left alone. Running it twice changes nothing the
second time.

If `settings.json` exists but is not valid JSON, the installer **refuses and leaves it
untouched** rather than overwriting a file it cannot understand.

---

## Uninstalling

Restore the backup next to the settings file:

```powershell
# Windows
cd $env:APPDATA\Vencord\settings
Copy-Item settings.json.bak-omni-<timestamp> settings.json -Force
```

```bash
# macOS
cd ~/Library/Application\ Support/Vencord/settings
cp settings.json.bak-omni-<timestamp> settings.json
```

Then delete `themes/OmniTheme.theme.css`. Discord must be closed for either.

The font is separate and outlives the theme — removing the theme does not remove it.
Leaving it installed is harmless; it is a font like any other. Removal instructions are in
the package README.
