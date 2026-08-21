# Customising

The whole theme is driven from a token block at the top of the stylesheet. Edit there,
not further down — everything else is wired to it.

Open `OmniTheme.theme.css` in any text editor. Vencord reloads the file the moment you
save it, so you can leave Discord open and watch changes land.

---

## The one that changes everything

```css
--omni-accent: oklch(0.606 0.213 302.6);   /* Omnivex violet */
```

The three numbers are lightness, chroma and **hue**. Change the hue — the last one — and
all nine derived shades move with it, staying on the same line.

| Hue | Result |
|---:|---|
| `302.6` | Omnivex violet *(default)* |
| `273.85` | Discord blurple |
| `25` | Red |
| `155` | Green |
| `80` | Amber |

This is why the ramp is in OKLCH rather than hex: nine hand-picked hex values drift apart
as soon as you adjust one, and you end up re-picking all of them.

---

## Transparency

```css
--omni-alpha: 0.94;
```

| Value | Result |
|---|---|
| `1.00` | Solid. No desktop showing through |
| `0.94` | Default — noticeable, still readable |
| `0.90` | Clearly tinted |
| `0.80` | Heavy. Expect to fight your wallpaper |

If small text becomes hard to read, **raise this before touching text colours** — those
are already at their contrast floor.

---

## Shape

```css
--omni-radius:    12px;   /* panels, buttons, inputs, cards */
--omni-radius-lg: 16px;   /* modals and large surfaces */
--omni-gap:        6px;   /* space around each floating panel */
```

`--omni-radius: 3px` gets you the original terminal look — sharp everything.

`--omni-gap` is per-panel, so the visible channel between two panels is twice the value.

> **Do not round the window edge.** `--omni-window-radius` exists and is `0` on purpose.
> The OS window underneath is square; rounding the page cuts transparent notches out of
> the corners while the real window edge stays put, and you see desktop between the two.

---

## Effects

```css
--omni-matrix:           1;      /* falling code: 0 disables */
--omni-matrix-opacity: 0.10;
--omni-matrix-speed:    42s;     /* higher = slower fall */

--omni-crt:              1;      /* scanlines + flicker: 0 disables both */
--omni-scanline-gap:   3px;
--omni-scanline-opacity: 0.06;
--omni-flicker-speed:   28s;     /* one twitch roughly every 14s */
```

**On a weaker machine,** `--omni-crt: 0` removes two of the three always-running
full-screen layers and is the single most effective change you can make.

> **If you retune the flicker,** raising `--omni-flicker-speed` makes it rarer *and*
> slower, because keyframe positions are relative. To change only the rarity, scale the
> burst percentages in `@keyframes omni-crt-flicker` down by the same factor. Doubling the
> speed without touching them stretches each blip from 70ms to 140ms.

---

## Type

```css
--omni-mono: "JetBrains Mono", "SF Mono", Menlo, "Cascadia Mono", ui-monospace, monospace;
--omni-sans: var(--omni-mono);
--omni-chat-size: 13px;
```

**For readable paragraphs while keeping the terminal chrome**, there is a commented line
next to `--omni-sans`:

```css
--omni-sans: "gg sans", "Inter", -apple-system, "Segoe UI", sans-serif;
```

`gg sans` is Discord's own face, so it is always present. This was tried as the default
and reverted — it made the message list read like stock Discord — but it is there if long
messages are what you care about.

---

## Signals

```css
--omni-dm-ring: 2px;   /* unread ring thickness; 0 restores the bar */
--omni-alert:   oklch(0.58 0.23 25);
```

---

## Where things live

The stylesheet is numbered in comments. If you are hunting for something:

| Section | Contains |
|---|---|
| 1 | **The token layer** — all the variables above |
| 5 | Layout surfaces, transparency, the window |
| 6–9 | Chat, sidebar, members, scrollbars |
| 11 | The CRT overlay — rain, scanlines, flicker |
| 20 | Alert language — mentions, unread, chips |
| 21 | Floating panels and the window edge |
| 23 | The DM unread ring |

---

## Two things to know before editing deeper

**Order matters more than usual.** Several surfaces are rounded *only* because their rule
comes after a corner-killing list near the top of the file. Move a section and you may
silently square something.

**Selectors match substrings, not whole names.** Discord's class names carry a build hash,
so rules target fragments. Substring matching does not respect word boundaries: a rule for
`pill` also matches `unreadPill` and `topPill`. Adding the `i` flag makes that worse. This
has already caused one rule in the file's history to quietly match only the things it was
never meant to.

---

## If you break it

Reinstall. The installer overwrites the theme file, and your Discord settings are
untouched by a theme edit.
