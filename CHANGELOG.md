# Changelog

Written for the person downloading the app, not for the people writing it —
internal refactors are omitted unless you would notice them. `release.sh` lifts
the section matching the version being released into the release notes, so this
file is where those notes are actually authored.

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
