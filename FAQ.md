# FAQ

---

### Why is this not free / not on GitHub?

It is donationware. The package is the thing being supported, so it is not published here
or anywhere else. This repository is the shop window rather than the shop.

The reasoning is simple: a theme that took months of work and 2,400 lines of documented
CSS is worth something, and the only leverage a solo author has is that the artefact is
not freely circulating. Support buys the package, and it buys continued development.

### Is it a subscription? Do I lose it if I stop?

No. A one-off Ko-fi contribution gets you the package. Patreon supports ongoing
development and gets you updates as they come, but **nothing you already have stops
working** if you stop. Support buys development, not permission to keep running what you
downloaded.

### Will this get my account banned?

No case of enforcement against a theme user is known — themes are, in practice,
universally tolerated. That said, client modification is outside Discord's Terms of
Service, and an observation is not a guarantee. You use it at your own risk. This is true
of every Discord theme, including free ones.

### Will it survive Discord updates?

Mostly, for a while. Discord's class names carry a build hash that changes with every
release, so themes are written against substrings that tend to be stable rather than the
full names. Small updates usually pass without incident. A significant redesign will break
parts of any theme, including this one, and it gets fixed when it happens.

### Does it work with BetterDiscord?

The stylesheet will load, but the installer does not touch BetterDiscord — it will tell
you so and point you at the folder to copy the file into by hand. The 52 plugins are
Vencord plugins and have no BetterDiscord equivalent, so that part will not apply.

### Why can't I snap the window to the side of my screen any more?

Window transparency and Aero Snap are mutually exclusive on Windows. A `transparent: true`
Electron window cannot truly maximise, so snapping has nothing to target and the maximise
button never changes icon. This is a Vencord/Electron limitation, not a theme bug —
tracked upstream at [Vesktop #896](https://github.com/Vencord/Vesktop/issues/896).

Three options, none of them free:

| | See-through | Snap works | Unfocused |
|---|---|---|---|
| Transparency on *(default)* | yes | **no** | stays translucent |
| Transparency off | no | yes | — |
| Windows Mica/Acrylic | yes | yes | **goes solid** |

The third looks like the best of both and is not: Windows renders Mica and Acrylic with a
solid fallback for inactive windows *by design*.

If you want tiling regardless, PowerToys FancyZones uses a different Windows API and is
unaffected.

### The installer window flashed for a second and nothing happened

You ran the `.ps1` directly. Use `INSTALL-WINDOWS.cmd` — it keeps the window open so you
can read the error, which was being printed all along. See
[Troubleshooting](docs/TROUBLESHOOTING.md).

### Can I turn off the falling code / scanlines / flicker?

Yes, each independently, one variable each: `--omni-matrix: 0`, `--omni-crt: 0`. They are
near the top of the stylesheet and documented in place.

### It uses a lot of GPU memory. Is something wrong?

No, and this was measured rather than guessed. Three always-running full-screen animated
layers — the falling code, the scanlines and the flicker — cost roughly 326 MB of GPU
memory on a 3840×1600 display, and the client never fully idles while they run.

That is inherent to the effects, not a bug: an infinitely-running animation promotes its
own compositing layer regardless of what you do. Containment and `will-change` removal
were both tried and measurably changed nothing.

On a weak machine, `--omni-crt: 0` removes two of the three layers.

### Can I change the colour?

One variable. `--omni-accent` is expressed in OKLCH; change the hue number and all nine
derived shades move with it, staying on-hue. That is the whole re-skin.

### Can I use it as a base for my own theme?

For yourself, freely — modify anything. Publishing a modified version for others is not
permitted. See [LICENSE.md](LICENSE.md).

### Does it collect anything?

No. There is no network call at runtime, no telemetry, no analytics, no update check. The
theme is a stylesheet and the installer touches only files on your own machine.

The plugin profile carries plugin *preferences* only — no tokens, no passwords. This was
verified rather than assumed, by scanning the profile for anything secret-shaped. One
field is deliberately excluded: `PinDMs.userBasedCategoryList`, which is keyed by Discord
account ID and holds pinned channel IDs. It is per-account data, not a preference, and it
would be meaningless — and yours — on someone else's machine.

### macOS?

**The theme works on macOS** — confirmed by a real Mac user. The installer's first real Mac
run did not: Finder refused it ("you do not have permission"), and a `sudo` attempt failed
on the shebang. Both were packaging defects — the zip carried no executable bit and had
Windows line endings — and both are fixed in the current build, which refuses to produce a
zip with either problem.

**The fixed installer has not yet been re-run on a Mac.** If you have one, run it with
`--dry-run` first and say what happens. If it fails on permission, `chmod +x
install-macos.command` from the extracted folder is the one-line workaround.

### I found a bug / it broke after a Discord update

Open an issue on this repository. Include your OS, your Discord and Vencord versions, and
a screenshot. Bug reports are genuinely useful; a fix by a particular date is not
promised.
