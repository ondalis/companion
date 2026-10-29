# Ondalis Companion 1.2.1

Published by **Ondalis**.

Ondalis Companion is the PC helper of the Ondalis apps. With **Ondalis PC Remote**, the phone app
that turns a phone into a keyboard, mouse, touchpad and media remote for a computer, it lets the app
list the PC's programmes and open them, receive the files you share from the phone and send files to it, shut the PC
down, restart it or put it to sleep, and drive its media and volume, on the same Wi-Fi, with
nothing to type on the PC. It is optional: the phone app works on its own over Bluetooth, with
nothing installed on the PC.

It stays local: no account, no cloud, no telemetry. It does nothing until your phone pairs with it
(a code shown on the PC, never sent over the network), and the connection is TLS, pinned to the
PC's own certificate. The only request it makes outside your network is the weekly check for a new
version described below, which you can turn off.

The companion is distributed as compiled programs only.

## What's new in 1.2.1

- **Send to phone:** a finished share no longer leaves its progress line in the window. A phone on
  Android 9 is named at once, in the window and in the icon's menu, as one that cannot receive files.
  The waiting line says what the phone needs: the same Wi-Fi, no VPN in the way.
- **Windows:** Explorer's "Send to" entry is named in the installer's language ("Téléphone
  (Ondalis)" in French); updating from 1.2.0 replaces the English one.

Installing 1.2.1 over 1.1.x or 1.2.0 keeps the pairing. From 1.1.0 or later, choose "Check for
updates" in the companion's menu or window, then "Update to 1.2.1".

## What's new in 1.2.0

- **Send to phone:** send files from the PC to your paired phone, from the "Send to phone" button in
  the companion's window, from "Send to" > "Phone (Ondalis)" in Windows Explorer, or from the
  right-click menu of Files (GNOME) and Dolphin (KDE). Photos and videos go to the phone's gallery,
  documents to Documents, the rest to Downloads; nothing is overwritten. The phone receives while
  Ondalis PC Remote is open or connected to the PC (Android 10 or later).

Installing 1.2.0 over 1.1.x keeps the pairing. From 1.1.0 or later, choose "Check for updates" in
the companion's menu or window, then "Update to 1.2.0".

## What's new in 1.1.2

- **Updates on Linux:** the installer window says when the update is done and closes by itself. Its
  close button no longer shows empty boxes.
- **After an update:** a notice tells you the companion was updated, on Windows and Linux.
- **A calmer look:** the amber glow behind the windows is gone.
- **Updates on Windows:** a PC that lacks the certificate of GitHub's servers no longer reports the
  update server as unreachable: Windows checks the certificate and fetches what it misses, as Edge
  does.

## What's new in 1.1.1

- **Linux:** a new window in the Ondalis look: the PC's state, updates, the pairing code and
  received files each in their own card.
- **Updates:** the window's switch now reads "Automatically", and the journal says "up to date" when
  there is nothing newer.

Installing 1.1.1 over 1.1.0 keeps the pairing. From 1.1.0, choose "Check for updates" in the
companion's menu or window, then "Update to 1.1.1".

## What's new in 1.1.0

- **Send to PC:** files you share from the phone land in your Downloads folder. The companion shows
  their progress and the time left, and tells you when they are in, with a button to open the
  folder.
- **Power:** shut down, restart or put the PC to sleep from the phone, now or at a time you choose,
  and turn its screens off. An app with unsaved work keeps the PC on.
- **Media and sound:** the phone drives the PC's players, its volume and its microphone.
- **More from the phone:** open a web address or a settings page on the PC, and put a text in its
  clipboard.
- **Updates:** the companion checks for a new version once a week (you can turn it off) and updates
  in one click. Each update is signed and checked before it runs.
- **Pairing:** the code shown on the PC is never sent over the network.
- **A new look:** the window and the installers in the Ondalis design, light and dark.
- **Windows:** an Allow button when the firewall blocked the companion, and no console window.
- **Linux:** the applications menu opens the companion's window, paired or not, and shows the new
  icon after an update.

Installing 1.1.0 over 1.0.x keeps the pairing.

## Files

- `ondalis-companion-setup.exe` — Windows 10 and 11, 64-bit.
- `ondalis-companion-linux.tar.gz` — Linux, x86-64, GTK desktops such as GNOME, whose system Python
  is 3.10, 3.11, 3.12, 3.13 or 3.14.
- `SHA256SUMS` — the checksums of the files above.
- `update.json` and `update.json.sig` — this release's description and its signature, which the
  companion reads to update itself.

macOS is not supported yet.

## Install on Windows

Run `ondalis-companion-setup.exe`. It installs for your user only, with no administrator rights,
into `%LOCALAPPDATA%\Programs\Ondalis Companion`, and adds "Ondalis Companion" to the Start menu.
At the end, leave "Launch Ondalis Companion" ticked: the companion starts and a small window shows
its pairing code. On your phone, in Ondalis PC Remote connected to this PC:
**Apps → Import apps → this PC**, then type the code. Closed, the window comes back with a click on
the companion's icon in the notification area (behind the ^ next to the clock); that icon's menu
also has Quit.

The companion starts with Windows: the installer offers it, ticked. To change that later:
Settings, Apps, Startup.

The first time it starts, Windows asks whether to let Ondalis Companion use your networks: choose
Allow, so your phone can reach it. Refused by mistake, the companion's window offers Allow again.
The program is not code-signed yet: Windows SmartScreen may say the publisher is unknown (More
info, then Run anyway).

To remove it: Settings, Apps, Ondalis Companion, Uninstall. Removing it also deletes its pairing
and its identity on this PC, so nothing secret is left behind: after a reinstall, pair the phone
again.

## Install on Linux

Extract the archive, then double-click "Install Ondalis Companion" in the extracted folder, or run:

```sh
tar xzf ondalis-companion-linux.tar.gz
./ondalis-companion/files/install.sh
```

No administrator rights and no download are needed: everything the companion uses comes in the
archive or with the desktop. The installer:

- installs the companion for your user only, under `~/.local/share/ondalis-companion`;
- lets the companion start by itself when your phone needs it, and stop when it is no longer used;
- adds "Ondalis Companion" to your applications, to open its window again.

On first install the companion opens and shows its pairing code. On your phone, in Ondalis PC
Remote connected to this PC: **Apps → Import apps → this PC**, then type the code.

To remove it: Uninstall in the companion's window, or `~/.local/share/ondalis-companion/uninstall.sh`.
Removing it also deletes its pairing and its identity on this PC (`~/.config/ondalis-companion`),
so nothing secret is left behind: after a reinstall, pair the phone again.

## Updates

Once a week, the companion asks GitHub whether a newer version is out: a plain HTTPS request that
carries nothing about you or your PC. A newer version is offered once, in a notification and in the
companion's menu ("Update to …"). One click downloads it, checks that Ondalis signed it and that the
file is the one signed, then installs it over the running companion: your pairing is kept. "Check
for updates" asks at once; "Check for updates automatically", in the icon's menu (and the window
on Linux), turns the weekly check off.

You can also update by hand: install the newer release over this one, as above.

## Verify your download

```sh
sha256sum -c SHA256SUMS
```

## Licences

On Windows, the installer shows which libraries are under the GNU LGPL (pystray, zeroconf), how to
replace them, and installs that notice (`LGPL-NOTICE.txt`) with `THIRD-PARTY-NOTICES.txt`, which
lists every component inside. On Linux, `THIRD-PARTY-NOTICES.txt` in the archive lists the
components it carries (cryptography, cffi, typing-extensions, unmodified, with their own licence
files in `deps/`), the terms of the Nuitka runtime inside the compiled modules, and the window's
typeface, Manrope, under the SIL Open Font License.
