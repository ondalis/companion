# Ondalis PC Remote — PC companion 1.0.0

Published by **Ondalis**.

The optional PC companion of **Ondalis PC Remote**, the phone app that turns a phone into a
keyboard, mouse, touchpad and media remote for a computer. The phone app works on its own over
Bluetooth, with nothing installed on the PC. On the same Wi-Fi, this companion lets the app list
the PC's programmes and open them, with nothing to type on the PC.

It stays local: no account, no cloud, no telemetry. It does nothing until your phone pairs with it
(a code shown on the PC, exchanged once for a token), and the connection is TLS, pinned to the PC's
own certificate.

The companion is distributed as compiled programs only.

## Files

- `ondalis-companion-setup.exe` — Windows 10 and 11, 64-bit.
- `ondalis-companion-linux.tar.gz` — Linux, x86-64, GTK desktops such as GNOME, whose system Python
  is 3.10, 3.11, 3.12, 3.13 or 3.14.
- `SHA256SUMS` — the checksums of the files above.

macOS is not supported yet.

## Install on Windows

Run `ondalis-companion-setup.exe`. It installs for your user only, with no administrator rights,
into `%LOCALAPPDATA%\Programs\Ondalis Companion`, and adds "Ondalis Companion" to the Start menu.
At the end, leave "Launch Ondalis Companion" ticked: the companion starts and a small window shows
its pairing code. On your phone, connected to this PC: **Apps → Companion → this PC**, then type
the code; the window closes by itself once the phone is paired. Closed earlier, it comes back with
a click on the companion's icon in the notification area (behind the ^ next to the clock); that
icon's menu also has Quit.

The companion starts with Windows: the installer offers it, ticked. To change that later:
Settings, Apps, Startup.

The first time it starts, Windows asks whether to let Ondalis Companion use your networks: choose
Allow, so your phone can reach it. The program is not code-signed yet: Windows SmartScreen may say
the publisher is unknown (More info, then Run anyway).

Installing a new version over a running companion closes it first; so does removing it.

To remove it: Settings, Apps, Ondalis Companion, Uninstall. Removing it also deletes its pairing
and its identity on this PC, so nothing secret is left behind: after a reinstall, pair the phone
again. Installing a new version keeps the pairing.

## Install on Linux

```sh
tar xzf ondalis-companion-linux.tar.gz
cd ondalis-companion && ./packaging/linux/install.sh
```

No administrator rights and no download are needed: everything the companion uses comes in the
archive or with the desktop. The installer:

- installs the companion for your user only, under `~/.local/share/ondalis-companion`;
- lets the companion start by itself when your phone needs it, and stop when it is no longer used;
- adds "Ondalis PC Remote" to your applications, to show the pairing code again.

On first install the companion opens and shows its pairing code. On your phone, connected to this
PC: **Apps → Companion → this PC**, then type the code.

To update it, run `install.sh` from the newer release: your pairing is kept.

To remove it: `./packaging/linux/uninstall.sh`. Removing it also deletes its pairing and its
identity on this PC (`~/.config/ondalis-companion`), so nothing secret is left behind: after a
reinstall, pair the phone again.

## Verify your download

```sh
sha256sum -c SHA256SUMS
```

## Licences

On Windows, the installer shows which libraries are under the GNU LGPL (pystray, zeroconf), how to
replace them, and installs that notice (`LGPL-NOTICE.txt`) with `THIRD-PARTY-NOTICES.txt`, which
lists every component inside. On Linux, `THIRD-PARTY-NOTICES.txt` in the archive lists the
components it carries (cryptography, cffi, typing-extensions, unmodified, with their own licence
files in `deps/`) and the terms of the Nuitka runtime inside the compiled modules.
