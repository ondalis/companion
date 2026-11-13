# Ondalis Companion 1.3.3

Published by **Ondalis**.

Ondalis Companion is the PC helper of the Ondalis apps. With **Ondalis PC Remote**, the phone app
that turns a phone into a keyboard, mouse, touchpad and media remote for a computer, it lets the app
list the PC's programmes and open them, receive the files you share from the phone and send files to it, shut the PC
down, restart it or put it to sleep, and drive its media and volume, on the same Wi-Fi, with
nothing to type on the PC. It is optional: the phone app works on its own over Bluetooth, with
nothing installed on the PC. With **Ondalis Share**, it sends files to the Ondalis Share devices on
your network and receives theirs.

It stays local: no account, no cloud, no telemetry. PC Remote's side does nothing until your phone
pairs with it (a code shown on the PC, never sent over the network), and the connection is TLS,
pinned to the PC's own certificate. A share from another device is asked on the PC first, and
"Can send to me" sets who may send. The only request it makes outside your network is the weekly check for a new
version described below, which you can turn off.

The companion is distributed as compiled programs only.

## What's new in 1.3.3

**Fixed**
- Windows: when the Windows firewall blocks the companion, its window now says so and lets you allow it. Before, nothing was shown.
- Windows: after your PC changes network, the companion can be found there again within seconds, without restarting it. Before, it sometimes stayed unreachable until restarted.

**Before you update**
- Updating keeps your phone paired.

## Files

- `ondalis-companion-setup.exe` — Windows 10 and 11, 64-bit.
- `ondalis-companion-linux.tar.gz` — Linux, 64-bit, GTK desktops such as
  GNOME: Ubuntu 22.04 or later, Debian 12 or later, Fedora 44 or later.
- `SHA256SUMS` — the checksums of the files above.
- `update.json` and `update.json.sig` — what the companion reads to
  update itself.

macOS is not supported yet.

## Install on Windows

Run `ondalis-companion-setup.exe`. It installs for your user only, with no administrator rights,
into `%LOCALAPPDATA%\Programs\Ondalis Companion`, and adds "Ondalis Companion" to the Start menu.
At the end, leave "Launch Ondalis Companion" ticked: the companion starts and its window opens. To
pair a phone, choose "Pair a phone" there: the window shows a code. On your phone, in Ondalis PC
Remote connected to this PC: **Apps → Import apps → this PC**, then type the code. Closed, the window comes back with a click on
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

On first install the companion's window opens. To pair a phone, choose "Pair a phone" there: the
window shows a code. On your phone, in Ondalis PC Remote connected to this PC: **Apps → Import
apps → this PC**, then type the code.

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
components it carries (cryptography, cffi, typing-extensions, ifaddr, unmodified, with their own licence
files in `deps/`), the compiler of its modules, Cython, whose output carries no licence condition, and
the window's typeface, Manrope, under the SIL Open Font License.
