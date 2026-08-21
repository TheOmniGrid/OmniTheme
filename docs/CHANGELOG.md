# Changelog

---

## 1.0.0 — 17 August 2026

First public release.

### The theme

- True `#000000` surfaces with hairline framing
- Omnivex violet accent, derived in OKLCH from a single hue
- Falling terminal code behind the client, spanning the full window width
- CRT scanlines with an occasional phosphor flicker
- JetBrains Mono end to end — 8 faces, bundled and installed per-user
- Adjustable window transparency, consistent whether focused or not
- Floating translucent panels with a violet rim glow around the window
- Unread DMs ring the sender's avatar; one shared alert language for mentions,
  unread counts and chips
- Contrast-checked text: 19.1:1 down to a 4.7:1 floor
- Every effect independently switchable from a single token block

### The installer

- One double-click on Windows; clears the downloaded-file mark itself
- Offers to close and reopen Discord rather than refusing to run
- Merges into your Vencord config, never replaces it — backs up, validates its own
  output, writes atomically
- Installs the font per-user, no administrator rights
- Names its failures specifically: BetterDiscord vs Discord-without-Vencord vs neither
- Idempotent — running it twice changes nothing the second time
- macOS installer included. Its first real Mac run failed on **packaging** — no executable
  bit and CRLF line endings, both invisible on Windows where the zip was built. Fixed in
  the build; the theme itself confirmed working on macOS; the fixed installer not yet
  re-run on a Mac

### Verification

Windows path verified end to end on Windows 11 and PowerShell 5.1, and independently by a
second user. The stylesheet is parsed in a real CSS engine before every release, with
landmark rules asserted present — a check that exists because a malformed comment once
silently swallowed a rule while every brace count passed.

---

<details>
<summary><strong>Pre-release history (2.x)</strong></summary>

The version numbering restarts at 1.0.0. Before that, the theme went through a long
private development cycle numbered 2.x, ending at 2.29.3 — the same package renumbered for
release.

Notable things that were found and fixed along the way, kept because they explain why
certain decisions are the way they are:

- **Transparency switched off whenever Discord lost focus.** Discord removes the
  `app-focused` class from `<html>` on blur; the theme was painting its backdrop on both
  `html` and `body`, and unfocused, two 15%-transparent layers composed to 97.75% opaque.
  One opaque layer, on `body`.
- **The falling code did not reach across wide displays.** It is text, not an image, so it
  never scaled — it simply ran out of characters. The stream was lengthened to cover
  3840px with margin.
- **The font stack was Mac-only.** Three named faces, none of which exist on Windows, so
  the theme silently rendered in Consolas. Fixed by bundling JetBrains Mono and installing
  it.
- **A malformed comment killed a rule.** Closed with `*/` then continued, so the following
  prose parsed as a selector and swallowed the rule after it. Undetected for two releases;
  it is why the stylesheet is now parsed by a real engine before every release.
- **A documented variable did nothing.** `--omni-matrix-width` was declared and described
  as controlling the rain's reach, and referenced nowhere.
- **A performance pass that mostly failed**, recorded honestly: containment and
  `will-change` removal changed the layer count and GPU memory not at all, because an
  infinitely-running animation promotes its own layer regardless. Style recalculation did
  get 7% faster.

</details>
