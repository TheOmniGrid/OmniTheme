# Screenshots — read before publishing any

**Internal note. Delete this file before the repository goes public, or keep it — it does
no harm — but the warning below is not optional.**

---

## The problem

A screenshot of your live Discord is a screenshot of **other people's personal data.**

One capture taken during preparation contained, on a single screen:

- **20+ real usernames** — friends, DM contacts, server members
- Their **avatars** (photographs of real people)
- Their **online/idle/DND status**
- **What games they were playing**, live
- Personal status lines, including *"If I'm not online, please leave me a message."*
- Server names revealing communities you and they belong to

None of those people agreed to appear on a public product page. Publishing that is a
privacy problem regardless of how good the theme looks in it, and in some jurisdictions
it is more than an etiquette problem.

**The raw captures in `assets/screenshots/` are unredacted. Do not publish them as-is.**

---

## Safe ways to get good shots

Ranked by how well they work.

### 1. A throwaway server (best)

Make a new Discord server. Add a few channels with generic names — `#general`,
`#announcements`, `#showcase`. Post a few messages from your own account. No other
members, no real conversations.

This gives you a realistic, populated-looking client with **nobody else's data in it**,
and you can compose the shot deliberately: an image embed to show media handling, a code
block to show the monospace, a mention to show the alert pulse.

### 2. Discord's own settings pages

Settings → Appearance, Accessibility, Voice & Video. These exercise the panels,
typography, toggles, sliders and the accent, with no personal data at all. Good for
detail shots; less good as a hero image.

### 3. Redact a real screenshot

Blur or block every username, avatar and status line. Tedious, easy to miss one, and a
missed one is the whole problem. Least recommended.

---

## Shots worth having

| Shot | Shows |
|---|---|
| **Hero** — full window, a channel with a few messages | The whole look in one image |
| **Falling code** — a quieter view where the rain reads clearly | The signature effect |
| **Unread ring** — DM list with one unread | The detail people notice |
| **Settings** — Appearance page | Typography, panels, controls |
| **Transparency** — over a visible desktop wallpaper | The effect that does not screenshot well otherwise |
| **Before/after** — stock Discord vs OmniTheme, same view | The most persuasive single image |

---

## Capture technique

Captures at 2× device scale are noticeably crisper than a plain screen grab, and the
tooling in the package repository can do it (`tools/discord-debug.ps1` plus a
`Page.captureScreenshot` call at `deviceScaleFactor: 2`).

Practical notes:

- Full window at 2× on a 3840-wide display produces roughly a 4 MB PNG. Downscale to
  ~1600–2000px wide for the README; keep the originals for Patreon and Ko-fi.
- The flicker fires roughly every 14 seconds and will not appear in most captures. That is
  fine — it is not a still-image feature.
- Transparency only reads if there is something behind the window. Put a wallpaper with
  some structure behind it, not a flat colour.
- Take the before/after pair in the **same view at the same window size**, or the
  comparison is worthless.

---

## Before you publish, check each image for

- [ ] Usernames, nicknames, display names
- [ ] Avatars of real people
- [ ] Server names and icons that identify communities
- [ ] Message content
- [ ] Status text and "playing" activity
- [ ] Your own email address (Settings → My Account shows it)
- [ ] Notification badges revealing who is messaging you
- [ ] Anything in the Windows taskbar or other windows if the shot is not cropped tight
