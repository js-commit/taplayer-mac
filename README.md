# TapLayer

Home row mods for macOS. Hold `a s d f j k l ;` for modifiers, tap them for
letters.

**[Download the latest release](https://github.com/js-commit/taplayer-mac/releases/latest)** ·
**[taplayer site](https://js-commit.github.io/taplayer-mac/)** · macOS 13+ ·
signed and notarized by Apple

| Hold | You get |
|---|---|
| `a` / `;` | Shift |
| `s` / `l` | Control |
| `d` / `k` | Option |
| `f` / `j` | Command |
| Space | Arrows on `ijkl`, page up/down, home/end, F1–F12 |
| Escape | Mouse layer — move the pointer, click, back/forward |
| Backtick | Scrolling, including horizontal |

Tap any of those keys and you get the letter, exactly as before.

## Why it exists

Typing into a Mac from an iPad or Android tablet over
[Jump Desktop](https://jumpdesktop.com/) means typing without a comfortable
Command key — and the usual macOS remapping tools cannot help, because they work
at the HID layer while those keystrokes arrive as synthetic events well above it.
TapLayer works at the layer they actually arrive on. It can remap the Mac's own
keyboards too, if you turn that on.

## Install

1. Open the dmg, drag **TapLayer** to Applications, launch it. A ⌨ icon appears
   in the menu bar — no window, no Dock icon.
2. Tick **TapLayer** in System Settings → Privacy & Security → **Accessibility**.
   Nothing is remapped until you do. It starts working the instant you flip the
   switch — no restart needed.
3. Typing from a tablet works immediately. For this Mac's own keyboard, turn on
   **Remap Local Keyboards** in the menu.

It adds itself as a login item on first launch; turn that off in the same menu.

**Kill switch:** `Left Ctrl` + `Space` + `Escape` stops the engine from anywhere,
including from the tablet. Quit is always in the menu too.

## What it does with your keystrokes

It is a keyboard remapper, so it sees what you type. Precisely:

- **It never records what you type.** The keystroke-logging diagnostics used
  during development are not compiled into release builds — it rejects those
  options outright rather than merely defaulting them off.
- **It has no network code.** Nothing is uploaded, because nothing can be.
- **Its log holds events, not text** — connections, layer changes, errors.
  Readable from the menu, private to your account, size-capped.
- **Modifiers stand down in password fields**, when macOS signals secure input.
- **Accessibility is the only permission it needs.** No root, no full disk
  access, no screen recording.

## Verifying the download

```sh
shasum -a 256 TapLayer-1.1.0.dmg
# d3c152a8dbdfb68d5ace3c2754ceadd75efcc24ba1f15f5a72398da803289815

spctl -a -t open --context context:primary-signature -vv TapLayer-1.1.0.dmg
# accepted / source=Notarized Developer ID
```

## Notes

Fast typing rolls fingers across the home row, which a naive hold-for-modifier
scheme turns into garbage. TapLayer waits out a short hold and watches for the
roll before committing, so ordinary prose types normally. The one thing that
still feels slower is capitalising many words in a row, since each capital waits
out the hold — the real Shift keys are still right there.

Free and unsupported, shared in case it is useful to someone else. Source is not
currently published.
