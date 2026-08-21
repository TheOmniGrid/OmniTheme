<p align="center">
  <img src="assets/brand/cover.gif" alt="OmniTheme — Discord, rebuilt as a terminal. The glyph cycles through all six accent variants." width="100%">
</p>

<h1 align="center">OmniTheme</h1>
<p align="center"><b>Discord, rebuilt as a terminal — true black surfaces, falling code, CRT scanlines, monospace end to end, and a transparent window onto your desktop.</b></p>
<p align="center">Part of the <a href="#the-omnivex-suite">OmniVex</a> suite.</p>

<p align="center">
  <a href="https://www.patreon.com/TheOmniGrid"><img alt="Get it on Patreon" src="https://img.shields.io/badge/Get%20it%20on-Patreon-FF424D?style=for-the-badge&logo=patreon&logoColor=white"></a>
  &nbsp;
  <a href="https://ko-fi.com/theomnigrid"><img alt="Get it on Ko-fi" src="https://img.shields.io/badge/Get%20it%20on-Ko--fi-FF5E5B?style=for-the-badge&logo=kofi&logoColor=white"></a>
</p>

<p align="center">
  <img alt="Version" src="https://img.shields.io/badge/version-1.0.0-8A7BFF?style=flat-square">
  <img alt="Platform" src="https://img.shields.io/badge/platform-Windows%20%7C%20macOS-0078D4?style=flat-square&logo=windows&logoColor=white">
  <img alt="Client" src="https://img.shields.io/badge/client-Vencord-8A7BFF?style=flat-square">
  <img alt="Telemetry" src="https://img.shields.io/badge/telemetry-none-2EA043?style=flat-square">
  <img alt="License" src="https://img.shields.io/badge/license-Donationware%20EULA-6A5BDB?style=flat-square">
</p>

<!-- Quick navigation. These are clickable: each chip jumps to a section of this
     page, or to the document it names. Anchors are GitHub's own slugs for the
     headings below -- if a heading is renamed, its chip has to be renamed too. -->
<p align="center">
  <a href="#how-to-get-it"><img alt="Get OmniTheme" src="https://img.shields.io/badge/⬇%20Get%20OmniTheme-8A7BFF?style=for-the-badge"></a>
  <a href="#features"><img alt="Features" src="https://img.shields.io/badge/Features-2B2545?style=for-the-badge"></a>
  <a href="#six-colours-one-theme"><img alt="Variants" src="https://img.shields.io/badge/Variants-2B2545?style=for-the-badge"></a>
  <a href="#requirements"><img alt="Requirements" src="https://img.shields.io/badge/Requirements-2B2545?style=for-the-badge"></a>
  <a href="docs/INSTALLATION.md"><img alt="Install" src="https://img.shields.io/badge/Install-2B2545?style=for-the-badge"></a>
  <a href="docs/FAQ.md"><img alt="FAQ" src="https://img.shields.io/badge/FAQ-2B2545?style=for-the-badge"></a>
  <a href="docs/CHANGELOG.md"><img alt="Changelog" src="https://img.shields.io/badge/Changelog-2B2545?style=for-the-badge"></a>
</p>

<!-- Real in-client screenshots are pending — see docs/SCREENSHOTS.md. The only captures
     taken so far show other people's real Discord data and must not be published. -->

---

## What it is

A complete visual replacement for the Discord client. Not a colour tweak — every
surface, every corner radius, every typeface and every piece of chrome has been
rebuilt around one idea: **Discord as a piece of terminal software.**

It ships as an installer that does the tedious part for you. One double-click sets up
the theme, installs the font it needs, and switches on a curated set of 52 Vencord
plugins with preferences already tuned. No manual copying, no settings archaeology.

## What makes it different

**It is not a recolour.** Most themes swap a palette and call it a day. This one
replaces the type stack, the corner language, the density, the surface model and the
window itself — 2,400 lines of stylesheet, every rule written against the live client
rather than guessed.

**It ships the font.** Themes that name a font they do not provide fail silently — the
client just renders in something else and you never find out. OmniTheme bundles
JetBrains Mono and installs it for you, per-user, with no administrator rights.

**It is documented like software, not like a skin.** Every non-obvious rule carries the
reasoning behind it. Change one variable and the entire client follows.

---

## Six colours, one theme

<div align="center">
  <img src="assets/variants.png" alt="The six OmniTheme accent variants" width="100%">
</div>

| Variant | Hue | |
|---|---:|---|
| **Omnivex violet** | 302.6 | the canonical build |
| **Discord blurple** | 273.85 | Discord's own brand hue |
| **Matrix green** | 142 | phosphor bright |
| **Space blue** | 245 | |
| **Blood red** | 25 | alerts move to amber |
| **Bee yellow** | 90 | honey, not lemon |

Every variant is the identical theme with one thing changed: the accent ramp, regenerated
from a single hue. Same rules, same plugins, same installer — a variant is a hue, not a
fork. Install one over another and it replaces cleanly.

Supporters get **all six** in one download. Details in [Variants](docs/VARIANTS.md).

## Features

### The look

| | |
|---|---|
| **True `#000000` surfaces** | Not "very dark grey". Actual black, on every base layer. |
| **Omnivex violet** | The whole accent ramp derived in OKLCH from a single hue, so every shade sits on the same line instead of drifting. |
| **Falling code** | An animated stream of terminal commands behind the entire client. |
| **CRT scanlines** | A drifting hairline grid, and an occasional phosphor flicker. |
| **Monospace end to end** | JetBrains Mono across the client — chat, chrome, menus, settings. |
| **A transparent window** | The desktop shows faintly through, at an adjustable strength. |
| **Floating panels** | Sidebar, chat and member list lifted off the backdrop as separate cards. |
| **Violet rim glow** | A soft accent light around the window edge. |

### The details most themes miss

- **Unread DMs ring the sender's avatar** with a pulsing red circle and a soft outside
  glow, sitting neatly *under* the status dot — instead of a bar off to the side.
- **Mentions, unread counts and "NEW" chips share one alert language**, so a red pulse
  always means the same thing wherever you see it.
- **Square, hairline-framed avatars and badges**, with the status notch preserved.
- **Attachment cards are quieter** than the messages they hang off.
- **Every effect has an off switch** — one variable each for the rain, the CRT layer,
  the transparency and the glow.

### The installer

- **One double-click.** It clears the Windows downloaded-file mark itself — the single
  most common reason a theme installer appears to do nothing.
- **Offers to close and reopen Discord**, because window transparency is a startup flag
  and a half-applied theme looks like a broken one.
- **Merges, never replaces.** Your other plugins, their settings and every unrelated key
  keep their values. It backs up first, validates its own output before writing, and
  writes atomically.
- **Refuses clearly.** No Vencord? It tells you whether you have BetterDiscord, Discord
  without Vencord, or neither — three different problems, three different messages.
- **Installs the font per-user.** No administrator prompt, ever.

---

## Requirements

| | |
|---|---|
| **Client** | [Vencord](https://vencord.dev/download) (or Vesktop), run at least once |
| **OS** | Windows 10/11, or macOS |
| **Discord** | Dark mode |
| **Admin rights** | Not required |

> **Windows only:** window transparency disables Aero Snap. This is a Vencord/Electron
> limitation, not a theme bug — a transparent window cannot truly maximise, so snapping
> has nothing to target. The theme documents how to turn transparency off if you would
> rather have snapping. See [FAQ](docs/FAQ.md).

---

## How to get it

OmniTheme is **donationware**. It is not on this repository, and there is no free
download link elsewhere — this page is the shop window, not the shop.

Supporting the work gets you the full package: the theme, the installer for both
platforms, the bundled font, and the documentation.

<p align="center">
  <a href="https://www.patreon.com/TheOmniGrid"><img src="assets/brand/support-patreon.svg" height="64" alt="Support OmniTheme on Patreon"></a>
  &nbsp;&nbsp;
  <a href="https://ko-fi.com/theomnigrid"><img src="assets/brand/support-kofi.svg" height="64" alt="Support OmniTheme on Ko-fi"></a>
</p>

Everything is built and maintained by one person. If it saves you an evening of fiddling
with CSS, that is roughly what it is worth.

---

## Documentation

| | |
|---|---|
| [**Features**](docs/FEATURES.md) | The full list, with what each thing actually does |
| [**Variants**](docs/VARIANTS.md) | The six colours, and how to make a seventh |
| [**Installation**](docs/INSTALLATION.md) | Step by step, both platforms |
| [**Customising**](docs/CUSTOMISING.md) | The variables worth knowing about |
| [**FAQ**](docs/FAQ.md) | Including the ones people actually ask |
| [**Troubleshooting**](docs/TROUBLESHOOTING.md) | When the window flashes and nothing happens |
| [**Changelog**](docs/CHANGELOG.md) | What changed and why |

---

## Legal

- **Licence:** proprietary donationware. See [LICENSE.md](LICENSE.md). Supporters get a
  personal-use licence; redistribution is not permitted.
- **Third-party components:** JetBrains Mono is bundled under the SIL Open Font Licence
  1.1. See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
- **Not affiliated with Discord.** Discord is a trademark of Discord Inc. This project is
  an independent client theme and is neither endorsed by nor connected to Discord Inc.
- **Not affiliated with Vencord** or any other client modification project.
- **Client modification** is outside Discord's Terms of Service. Themes are, in practice,
  universally tolerated, but you use this at your own risk.

---

## The OmniVex suite

OmniTheme is one of a family of tools sharing a design language and a philosophy —
modern, fast, no telemetry:

**OmniTheme** · **OmniBlock** · **OmniCleaner** · **OmniAPO** · **OmniEQ** · **OmniPlay** · **OmniScale** · **OmniShade** · **OmniVisuals** · **OmniGPU** · **OmniWrappers**

<sub>**OmniWrappers** is four Direct3D compatibility installers — OmniDXVK, OmniDxWrapper, OmniVKD3D and OmniVoodoo2.</sub>

<sub>Tuned for framerate, mixed for headroom, sharp to the pixel. Donationware
tools for gamers and audiophiles — audio, graphics, and a bit of privacy too.</sub>

More at [github.com/TheOmniGrid](https://github.com/TheOmniGrid).

---

## Credit

OmniTheme is an original theme — no Discord, Vencord or third-party theme code is
included in it or derived from it.

It bundles **[JetBrains Mono](https://github.com/JetBrains/JetBrainsMono) 2.304** by
the JetBrains Mono Project Authors, under the **SIL Open Font Licence 1.1**, unmodified.
**Cascadia Mono** (© Microsoft Corporation, SIL OFL 1.1) is named as a fallback but not
bundled.

Full attribution in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

---

## Contact

Bug reports are genuinely useful — [open an issue](../../issues/new/choose) and include
your OS, your Discord and Vencord versions, and a screenshot. A fix by a particular date
is not promised.

Licensing questions, permissions, or anything the licence does not cover:

**omnivex@theomnigrid.biz**

---

<div align="center">

Copyright © 2026 OmniVex · Proprietary donationware · Discord is a trademark of Discord Inc.; OmniTheme is not affiliated with Discord Inc. or the Vencord project.

</div>
