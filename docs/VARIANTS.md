# Variants

Six accents. One theme. Supporters get all of them in a single download.

<div align="center">
  <img src="../assets/variants.png" alt="The six OmniTheme accent variants" width="100%">
</div>

---

## The six

All six ship in the one package. The installer asks which you want — or takes it as an
option — and installs that one. Enter picks violet.

| Variant | Pick | Accent | Alerts |
|---|---|---|---|
| **Omnivex violet** | `1` / `violet` | `oklch(0.606 0.213 302.6)` | red |
| **Discord blurple** | `2` / `blurple` | `oklch(0.606 0.213 273.85)` | red |
| **Matrix green** | `3` / `matrix` | `oklch(0.780 0.240 142)` | red |
| **Space blue** | `4` / `space` | `oklch(0.606 0.213 245)` | red |
| **Blood red** | `5` / `blood` | `oklch(0.580 0.230 25)` | **amber** |
| **Bee yellow** | `6` / `bee` | `oklch(0.800 0.190 90)` | red |

**Omnivex violet** is the canonical build — the one the theme was designed in. **Discord
blurple** is Discord's own brand hue, for anyone who wants the terminal treatment without
leaving the colour they know.

---

## They really are the same theme

Each variant is the canonical package with exactly one thing regenerated: the nine-line
accent ramp at the top of the stylesheet, derived from a single OKLCH hue. Every other
rule, every plugin preference, every installer file is byte-identical across all six.

That is not a marketing claim — it is how they are built. A script regenerates every
variant from the one source, and it refuses to run unless regenerating the canonical hue
reproduces the canonical file byte for byte. A variant is a hue, not a fork, so a fix to
the theme reaches all six by rerunning the build.

**Two variants carry a deliberate second change**, stated so nobody goes looking for a bug:

- **Matrix green and Bee yellow are lifted in lightness** — 0.78 and 0.80 against the
  canonical 0.606. At the canonical lightness those hues read dim and muddy, not the
  colours named. The lift makes the accent *be* the colour rather than a dark cousin of it.
- **Blood red swaps the alert colour to amber.** Mention badges, unread counts and the
  DM ring are all the same red as the new accent and would vanish into it. That variant
  alone moves alerts to hue 80.

---

## Why OKLCH

Because the whole ramp is one number.

The accent and its eight derived shades — hover, active, light, dim, and four
transparencies for tints, borders and glow — are all expressed as lightness, chroma and
**hue** in OKLCH. Change the hue and every shade moves with it, staying on the same
perceptual line.

Nine hand-picked hex values would drift apart the moment you adjusted one, and you would
end up re-picking all of them. This is why a variant is a hue and not a fork, and it is
also why you can make your own.

---

## Switching between them

Run the installer again and pick a different one — or pass it directly:

```powershell
.\install-windows.ps1 -Colour matrix        # Windows
./install-macos.command --colour matrix     # macOS
```

Every variant is installed under the same filename — `OmniTheme.theme.css` — with the same
`@name`, so Vencord shows **one** theme rather than six, and the new file replaces the old
one instead of leaving two enabled themes fighting over the same selectors.

Your plugins and settings are untouched; the installer merges, it does not replace.

Which variant you have is stated in the stylesheet header: the `@description` line ends
*"re-lit in Matrix Green"*, or whichever it is.

---

## Making a seventh

Open `OmniTheme.theme.css` in any text editor. Near the top:

```css
--omni-accent: oklch(0.606 0.213 302.6);
```

Change the last number. Vencord reloads the file the moment you save, so leave Discord
open and watch it land.

| Hue | Result |
|---:|---|
| `0` | Pink-red |
| `25` | Red |
| `55` | Orange |
| `90` | Yellow |
| `142` | Green |
| `195` | Cyan |
| `245` | Blue |
| `273.85` | Discord blurple |
| `302.6` | Omnivex violet |
| `330` | Magenta |

Two things worth knowing if you go further than the hue:

- **Green and yellow want more lightness.** OKLCH treats them as perceptually light hues,
  so at 0.606 they look dim. Raise the first number toward 0.78–0.80.
- **If your accent is red, move the alerts.** `--omni-alert` is red; find it further down
  and pick another hue, or badges and the unread ring disappear into the accent.

The full customising guide is in [CUSTOMISING.md](CUSTOMISING.md).
