# Troubleshooting

Every failure below prints a message. The most common problem is not seeing it.

---

## The PowerShell window flashes and nothing happens

**The single most common report, and it is not a bug in the installer.** The error is
being printed correctly, to a window that closes before you can read it.

**Fix:** use `INSTALL-WINDOWS.cmd` rather than the `.ps1`. It keeps the window open at the
end so the reason is readable, and it clears the downloaded-file mark first.

The underlying cause is usually this: a zip that arrived over Discord, email or a browser
has every file inside it marked untrusted by Windows, and PowerShell refuses the script
**even with `-ExecutionPolicy Bypass`**. The `.ps1` cannot clear that mark for itself,
because Windows will not run it until the mark is cleared.

By hand, in the extracted folder:

```powershell
Get-ChildItem -Recurse | Unblock-File
```

Copying the zip on a USB stick avoids the mark entirely.

---

## "running from inside the zip, not from an extracted folder"

Explorer's zip preview looks like a folder and is not. Double-clicking inside it copies
one file to a temp directory without its siblings and runs it there.

**Fix:** right-click the zip → *Extract All*, open the extracted folder, run it from there.

---

## "no Vencord or Vesktop folder found"

The installer distinguishes three different situations and tells you which one you are in:

| It says | What to do |
|---|---|
| BetterDiscord is installed, Vencord is not | Copy the `.css` by hand into `%APPDATA%\BetterDiscord\themes`. The 52 plugins will not apply — they are Vencord plugins |
| Discord is installed, Vencord is not | Install [Vencord](https://vencord.dev/download), **run Discord once**, then retry |
| Neither found | Install Discord, then Vencord |

The "run once" step matters: Vencord creates its folder on first run, and the installer
has nothing to write into before that.

---

## "Discord is running"

Answer `Y` and the installer will close it and reopen it when finished.

This is not fussiness. Vencord holds `settings.json` in memory and rewrites it on quit, so
anything written underneath a live client is silently discarded. Reopening matters too —
window transparency is a startup flag, so a client that was only reloaded shows a
half-applied theme, which looks exactly like a failed install.

---

## The theme installed but Discord looks unchanged

1. **Check it is enabled:** Vencord → Themes → *OmniTheme* should be ticked.
2. **Check dark mode:** Settings → Appearance → Dark. The theme is dark-only.
3. **Quit Discord fully and reopen** — from the tray icon, not the window X, which only
   minimises. A reload is not enough for the transparency flag.

---

## Another theme is fighting it

Two full themes will contest the same selectors and the result is unpredictable. Turn the
other one off in Vencord → Themes.

The installer deliberately preserves any theme you already had enabled rather than
silently disabling it — so if you had one, it is still on.

---

## The text is not in the right font

Check Vencord → Themes shows no error, then quit and reopen Discord. Newly installed fonts
are picked up by processes started afterwards.

If you installed with `--no-font` / `-NoFont`, the theme falls back to Cascadia Mono
(Windows 11) or whatever monospace your system provides. That is a fallback, not the
intended look.

---

## Small text is hard to read against my wallpaper

Window transparency means text sits on whatever your desktop is doing, and a busy
photograph will win against small type.

**Raise `--omni-alpha`** before touching any text colours — those are already at the
contrast floor and have no room left. `1.00` is fully solid.

---

## Something looks misaligned after a Discord update

Discord rerolls its class name hashes on every release. Most of the theme matches on
stable substrings and survives, but a significant redesign will move things.

Report it with a screenshot and your Discord version. Include what the element is called
if you know — that is the part that takes longest to find.

---

## I want to undo everything

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

The backup is created before the installer writes anything, so it restores your plugin
setup exactly as it was.

---

## Still stuck

Open an issue with:

- Your OS and version
- Discord version and Vencord version
- **The full text of the installer window** — this is the useful part
- A screenshot if it is visual
