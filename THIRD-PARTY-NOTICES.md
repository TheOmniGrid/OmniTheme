# Third-party notices

OmniTheme bundles and depends on work by others. This file records what, under which
terms, and what those terms require of anyone redistributing the package.

---

## Bundled: JetBrains Mono

**Included in the OmniTheme package** (8 font files in `fonts/`), installed per-user by
the installer.

| | |
|---|---|
| **Copyright** | © 2020 The JetBrains Mono Project Authors |
| **Project** | https://github.com/JetBrains/JetBrainsMono |
| **Version** | 2.304 |
| **Licence** | SIL Open Font Licence, Version 1.1 |
| **Full text** | `fonts/OFL.txt` in the package |
| **Authors** | `fonts/AUTHORS.txt` in the package |

The SIL OFL explicitly permits bundling and redistribution as part of a larger work,
including one that is sold or supported by donations. It requires that the copyright
notice and licence text travel with the font files — both do, in `fonts/`.

**The font files are not modified.** They are the upstream release, unrenamed.

> **This is important and easy to get wrong:** the OFL terms apply to the font
> regardless of OmniTheme's own licence. Nothing in OmniTheme's proprietary licence
> restricts your rights to JetBrains Mono. You may extract those files and use them
> freely under the OFL. The OFL's one prohibition is selling the fonts *by themselves*.

## Named but not bundled: Cascadia Mono

Referenced as a fallback in the theme's font stack. It ships with Windows 11 and is not
included in the package. Also SIL OFL 1.1, © Microsoft Corporation.

---

## Not bundled, not affiliated

### Discord

OmniTheme is an independent client theme. It is **not affiliated with, endorsed by,
sponsored by, or connected to Discord Inc.** in any way.

"Discord" is used solely to identify the application the theme applies to, which is
nominative use. No Discord trademark, logo, wordmark or brand asset is included in or
distributed with OmniTheme.

Modifying the Discord client falls outside Discord's Terms of Service. See
[LICENSE.md](LICENSE.md) §6.

### Vencord / Vesktop

OmniTheme is a theme *for* Vencord and is **not affiliated with the Vencord project**.
Vencord is licensed GPL-3.0; no Vencord code is included in, derived from, or distributed
with OmniTheme. A CSS theme loaded by an application is not a derivative work of that
application.

The installer reads and writes Vencord's own configuration files on the user's machine.
It does not bundle, patch or redistribute Vencord itself.

### BetterDiscord

Mentioned in the installer's diagnostics only, to tell a user which client modification
they actually have. No affiliation, no bundled code.

---

## Summary for redistributors

You may not redistribute OmniTheme (see [LICENSE.md](LICENSE.md)). If permission is ever
granted, these obligations travel with it:

1. `fonts/OFL.txt` and `fonts/AUTHORS.txt` must be included, unmodified
2. The JetBrains Mono files must not be renamed or sold standalone
3. The Discord non-affiliation statement must not be removed
4. OmniTheme's own copyright notice must remain in the stylesheet header

---

*Last updated: 2026-08-17 · OmniTheme 1.0.0*
