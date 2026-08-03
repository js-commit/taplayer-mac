# TapLayer

**Every modifier under a finger that is already resting there — on your Mac's
keyboard, and on the tablet you are driving it from.**

Hold `a s d f j k l ;` for modifiers. Tap them and you get the letter, exactly
as before.

**[Download the latest release](https://github.com/js-commit/taplayer-mac/releases/latest)** ·
**[taplayer site](https://js-commit.github.io/taplayer-mac/)** · macOS 13+ · free

---

## Leave the laptop at home

Remote into your Mac from an iPad or an Android tablet over
[Jump Desktop](https://jumpdesktop.com/) and you have your whole desktop in a bag
that weighs nothing — except that the keyboard you brought is not really a Mac
keyboard. Android will not forward `⌘` at all. There is no trackpad on a lot of
folio cases. Nothing is where your hands expect it.

TapLayer fixes that from the Mac side, and works the same way on the MacBook's
own keyboard, so the muscle memory carries over.

### Android never gives you Command

Android OS swallows the Command key before Jump Desktop can forward it — `⌘Tab`,
`⌘C`, `⌘Space`, all dead. You are left with Control and a pile of workarounds.
TapLayer puts Command on `f` and `j`, and rewrites the tablet's Alt key into
Command as well, so the normal Mac shortcut vocabulary comes back. iPadOS is
less bad about this, but not by much.

### A keyboard with no trackpad, and no mouse to pack

Hold `Esc` and the letters become a mouse — `ijkl` move the pointer with
acceleration, `f` left-clicks, `r` right-clicks, `y`/`h` scroll, `q`/`w` go back
and forward. Enough to actually use a Mac. A Smart Folio without a trackpad
stops being a compromise.

### Your small keyboard doesn't need QMK or ZMK

Home row mods are normally a firmware feature, and most compact boards ship with
firmware you cannot touch. TapLayer does the work on the Mac instead, so any
keyboard gets them.

### Reading, not just typing

Hold `` ` `` and the arrow keys become a scroll wheel, horizontal included,
accelerating the longer you hold. Long articles go by without your hand leaving
the keyboard.

## The keymap

Fixed for now — one opinionated default set, nothing to configure and nothing to
get wrong. Custom layouts are the next thing being built.

**Home row** — tap for the letter, hold for the modifier:

| Hold | You get |
|---|---|
| `a` `;` | Shift |
| `s` `l` | Control |
| `d` `k` | Option |
| `f` `j` | Command |

**Hold `Space`** — navigation:

| Key | Does |
|---|---|
| `i` `j` `k` `l` | ↑ ← ↓ → |
| `y` `h` | Page up / page down |
| `u` `o` | Home / End |
| `e` `n` | Return / Escape |
| `f` `g` `r` `c` | `/` `?` `'` `_` |
| number row | F1–F12 (`-` and `=` are F11 and F12) |

**Hold `Esc`** — mouse:

| Key | Does |
|---|---|
| `i` `j` `k` `l` | Move the pointer (accelerates while held) |
| `f` `r` | Left click / right click — double and triple clicks work |
| `y` `h` | Scroll up / down |
| `q` `w` | Browser back / forward |
| arrows, delete | Same thing, if your keyboard has the cluster |

**Hold `` ` ``** — arrow keys become a scroll wheel, horizontal included.

**Odds and ends:**

| | |
|---|---|
| Option + tap `Space` | Delete the word behind the cursor |
| Caps Lock (Android) | Becomes Escape, since Android eats the real one as Back |
| Alt (Android) | Becomes Command, automatically, for Android sessions only |
| `Left Ctrl` + `Space` + `Esc` | Kill switch — stops the engine from anywhere, including from the tablet |

## Why not kanata or Karabiner

Those are good tools and far more configurable than this one. The catch is the
layer they work at: they remap physical keyboards by grabbing the HID device
underneath, but keystrokes from a tablet never touch HID. Jump Desktop injects
them further up, so kanata never sees them, and no amount of configuring changes
that. TapLayer sits at the layer they actually arrive on.

| | TapLayer | kanata |
|---|---|---|
| Keys from an iPad or Android over Jump Desktop | works | never sees them |
| The Mac's own keyboards | works | works |
| What you install | one app | kanata, plus Karabiner's DriverKit virtual keyboard driver |
| Permissions to grant | Accessibility | a driver extension, Input Monitoring, and Accessibility — the last two through a foreground priming dance, because a root daemon cannot raise its own prompts |
| Runs as | you, one process | root, as a LaunchDaemon |
| Setup time | a minute | an afternoon, honestly |
| Custom keymaps | not yet — coming | yes, and it is genuinely good at it |

If you only ever type on the Mac's built-in keyboard and want a fully custom
layout, kanata is worth the afternoon. If you want home row mods to just be
there, on whatever keyboard you happen to be holding, this is the smaller thing.

## Install

1. Open the dmg, drag **TapLayer** to Applications, launch it. A ⌨ icon appears
   in the menu bar — no window, no Dock icon.
2. Tick **TapLayer** in System Settings → Privacy & Security → **Accessibility**.
   Nothing is remapped until you do. It starts working the instant you flip the
   switch — no restart needed.
3. Typing from a tablet works immediately. For this Mac's own keyboard, turn on
   **Remap Local Keyboards** in the menu.

It adds itself as a login item on first launch; turn that off in the same menu.

## Privacy

**No network. No keystroke logging.** There is no networking code in the app at
all, so nothing can be uploaded even by accident, and the ability to record what
you type is not compiled into this build. The log holds events — connections,
layer changes, errors — never text, and you can open and read it yourself from
the menu. Accessibility is the only permission it asks for: no root, no full disk
access, no screen recording. Modifiers also stand down entirely whenever macOS
signals a secure input field.

## Notes

Fast typing rolls fingers across the home row, which a naive hold-for-modifier
scheme turns into garbage. TapLayer waits out a short hold and watches for the
roll before committing, so ordinary prose types normally. The one thing that
still feels slower is capitalising many words in a row, since each capital waits
out the hold — the real Shift keys are still right there.

Free and unsupported, shared in case it is useful to someone else. Source is not
currently published.
