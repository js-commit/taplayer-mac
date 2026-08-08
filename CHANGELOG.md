# Changelog

Written for the person downloading the app, not for the people writing it —
internal refactors are omitted unless you would notice them. `release.sh` lifts
the section matching the version being released into the release notes, so this
file is where those notes are actually authored.

## 1.3.0

- **Every key is rebindable.** Settings → Edit Keymap opens a keyboard grid:
  click a key, pick what it should do — tapped and held, on the base layer or
  on any of the three hold layers. Until now the keymap was whatever we
  decided it was, and the only answer to "I want Escape somewhere else" was
  no.
- **The keymap is a file you own.** Everything the editor writes lands in
  `~/.config/taplayer/taplayer.toml`, plain text, hand-editable, and fine to
  keep in a dotfiles repo. `taplayer config show` prints the shipped keymap to
  start from and `taplayer config validate` checks your edits with
  line-and-column errors. No file means the built-in keymap, exactly as
  before — nothing to do if you liked it.
- **A broken keymap can't wedge your keyboard.** If the file doesn't parse,
  the engine keeps the built-in keymap, the menu-bar icon shows an amber dot,
  and the menu tells you which line is wrong. Restarting onto a broken file is
  refused outright rather than done halfway.
- **Separate keymaps per device.** The iPad, an Android tablet, and your Mac's
  own keyboard each get their own profile, as tabs in the editor. Bind Caps
  Lock one way for the tablet and another way at your desk.
- **Hold and tap timings are adjustable**, in the same window — how long a
  hold takes to register, and how long after typing home row mods stay out of
  the way. Previously command-line flags that vanished at every login.
- **The Android workarounds finally stick.** Caps-as-Escape and
  Option-as-Command are settings in the keymap file now, so turning one off
  survives a restart. Set as command-line flags they reverted every login,
  silently.
- Fixed: on the mouse layer, browser back and forward could keep firing after
  you let go of Escape.

Home row tap-versus-hold behaves exactly as it did in 1.2.0. If you never open
the editor, this release changes nothing about how the app types.

## 1.2.0

- **A setup window on first launch.** TapLayer now walks you through granting
  Accessibility instead of starting up silent. Before, if you missed the
  permission prompt, the app looked like it had done nothing at all — it was
  running, but remapping nothing, with no way to tell. That was the most
  confusing thing about installing it, and it is gone.
- **It asks where you type from, and remembers.** If you use TapLayer on a
  keyboard attached to your Mac rather than through a tablet, choose that once
  during setup — no hunting for a menu toggle, and the choice survives
  restarts and logins. (Support for remote-desktop apps besides Jump Desktop
  is coming.)
- **A Settings window**, in the menu-bar icon. Turn individual layers on or off
  — mouse, navigation, scroll, the cursor ring, Option+Space delete — without
  touching the command line. Custom per-key mappings will live here next.
- **No cursor ring when you are at your own Mac.** The orange ring exists so a
  tablet can see where the pointer went in a video stream. Sitting at the
  machine, it was just a distraction. Remote sessions still get it.
- If you type on the Mac's own keyboard, TapLayer now suggests binding Caps
  Lock to Escape, and links you straight to the setting. It puts Escape under
  your pinky — which is also the key you hold for the mouse layer.

Nothing about how home row mods decide tap-versus-hold changed.

## 1.1.2

- Fixes install on macOS 13, 14, and 15. Earlier downloads were built in a
  way that made Finder refuse them on anything older than macOS 26 with
  "You can't use this version of the application". The app now installs and
  runs on macOS 13.0 (Ventura) and later, as the requirements always said.

Nothing about how keys are remapped changed in this release.

## 1.1.1

- **Open Log** now follows wherever the running engine's output is really
  going, and greys out when that file has been deleted or moved. Before, the
  menu item could stay clickable and silently open nothing — or, after a log
  rotation, open the wrong file.
- Log rotation now runs on every background launch, including the tray's own
  **Restart Engine**, which had been skipping it.
- New landing page and README, which say what the app is for rather than only
  what it does.

Nothing about how keys are remapped changed in this release.

## 1.1.0

- Menu-bar toggle for **Remap Local Keyboards**, remembered across restarts, so
  the Mac's own keyboards can be switched in and out without touching the CLI.
- **Restart Engine** in the menu.
- The log rotates at 5 MB (one `.old` kept) and every line carries a wall-clock
  timestamp.

## 1.0.0

First release. Home row modifiers, the Space nav layer, the Escape mouse layer,
the backtick scroll layer, and a menu-bar app to hold them.
