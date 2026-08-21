# Features

Everything OmniTheme changes, and what each thing is actually for.

---

## Surfaces and colour

**True `#000000` base.** Every base layer is actual black rather than dark grey. The
columns are separated by a hairline frame instead of tonal steps, which is why the frame
matters more here than it would on a grey base.

**Omnivex violet.** The accent and its eight derived shades are expressed in OKLCH from a
single hue number. Change that number and the whole ramp moves together, staying on-hue —
hand-picked hex values drift apart as soon as you adjust one.

**Contrast-checked text.** Every text colour is measured against `#000000`, not chosen by
eye: primary 19.1:1, secondary 11.2:1, muted 7.1:1, dim 6.0:1, ghost 4.7:1. The floor is
deliberate — ghost carries timestamps and placeholders and sits just above the WCAG AA
threshold for small text.

**Adjustable transparency.** The window is see-through onto your desktop, at a strength
you control. It stays consistent whether Discord is focused or not (which took finding —
see the changelog).

---

## Type

**JetBrains Mono, bundled and installed.** Eight faces: Regular, Medium, SemiBold and
Bold, each with a matching italic, so nothing is synthetically bolded or slanted.
Installed per-user, no administrator prompt.

The font is shipped rather than merely named because Discord's content security policy
blocks webfont requests. A theme that asks for a font it does not provide does not fail
loudly — it quietly renders in whatever the OS substitutes, and you may never notice.

**Size compensation.** Monospace runs wider than Discord's own UI font, so every sized
piece of text is re-tuned rather than left to overflow. The floor is 10px; nothing smaller.

---

## Motion and texture

| Effect | What it is | Switch |
|---|---|---|
| **Falling code** | A stream of terminal commands drifting behind the client | `--omni-matrix` |
| **Scanlines** | A drifting hairline grid across every surface | `--omni-crt` |
| **Phosphor flicker** | An occasional brightness twitch, roughly every 14 seconds | `--omni-crt` |
| **Alert pulse** | Unread and mention markers breathe rather than sit still | — |

All of it sits *behind* your content. Images, embeds and link previews are never drawn
over — that took a specific technique (a negative z-index inside a deliberately created
stacking context) because Discord wraps the message list in containers that defeat the
obvious approach.

Every animation honours `prefers-reduced-motion`. Motion is the decoration; the colour
still carries the meaning without it.

---

## Layout

**Floating panels.** The server rail, channel sidebar, chat and member list are separate
cards with hairline borders, rounded corners and a 12px channel between them. They are
translucent rather than opaque, so the falling code passes faintly through each card and
shows at full strength in the gaps — which is what makes them read as lifted rather than
drawn on.

**Square window edge.** Deliberately. Rounding the page does not round the window: the OS
window underneath stays square, so a radius on the page cuts transparent notches out of
the corners while the real window edge stays put. Matching the window is the only thing
that looks right.

**Violet rim glow** around the window edge, as an inset light.

---

## Signals

**Unread DMs ring the sender.** A pulsing red circle with a soft outside glow appears
around the avatar of whoever messaged you, sitting under the online/idle/DND dot — rather
than a bar off to one side. Only the conversation that is actually unread is marked.

**One alert language.** Mention counts, unread indicators and "NEW" chips all use the same
red and the same pulse, so the signal means one thing wherever it appears.

**Live is green, not red.** The voice/audio badge is deliberately green and deliberately
still: it is a status you glance at, not something asking to be dismissed.

---

## The 52 plugins

The installer switches on a curated Vencord plugin set with preferences already tuned —
quality-of-life fixes, sensible privacy defaults, and UI improvements that suit the theme.

**It merges rather than replaces.** Plugins you already had stay enabled, their settings
are untouched, and every unrelated key in your config keeps its value. Run it twice and
the second run changes nothing.

Prefer to keep your own plugin preferences? `--no-plugin-settings` turns the plugins on
without touching how they are configured.

---

## Customising

The whole theme is driven from a token block at the top of the file. The dials worth
knowing:

| Variable | Effect |
|---|---|
| `--omni-accent` | Re-skin everything. One hue number; all nine shades follow |
| `--omni-alpha` | Window transparency, 1.00 solid → 0.80 heavy |
| `--omni-radius` | Corner rounding across the client |
| `--omni-matrix` | Falling code on/off |
| `--omni-crt` | Scanlines and flicker on/off |
| `--omni-gap` | Space between the floating panels |
| `--omni-dm-ring` | Unread ring thickness |

See [CUSTOMISING.md](CUSTOMISING.md) for the rest.

---

## What it does not do

Stated plainly, because a feature list that only lists wins is not much use:

- **It does not round the OS window.** That needs a flag the application sets at creation,
  which no stylesheet can reach.
- **Window transparency disables Aero Snap on Windows.** A Vencord/Electron limitation, not
  a theme bug. Turning transparency off restores snapping.
- **It cannot survive every Discord update.** Discord's class names carry a build hash that
  is rerolled on each release. Most of the theme matches on stable substrings, but a
  significant redesign will break parts of any theme.
- **It is dark-mode only.** Discord must be set to dark; a light-mode variant does not exist.
