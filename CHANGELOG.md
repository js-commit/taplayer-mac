# Changelog

Written for the person downloading the app, not for the people writing it —
internal refactors are omitted unless you would notice them. `release.sh` lifts
the section matching the version being released into the release notes, so this
file is where those notes are actually authored.

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
