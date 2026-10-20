# Beavers — Downloads

This is the official **download and auto-update channel** for **Beavers**, a lightweight,
privacy-respecting local World of Warcraft combat-log analyzer and WarcraftLogs report viewer.

Beavers is **proprietary, closed-source software** — free to download and run, but not open source.
This repository hosts release binaries only; there is no source code here. See [`LICENSE`](LICENSE)
for the full terms.

## Install

Grab the latest build from the [Releases](../../releases) page.

- **Linux (AppImage — any distro, including Arch)** — download the `.AppImage` from
  [Releases](../../releases), then:
  ```bash
  mv beavers_*.AppImage Beavers.AppImage   # optional, see below
  chmod +x Beavers.AppImage
  ./Beavers.AppImage
  ```
  The AppImage updates itself in-app by replacing the file **in place**. Any shortcut or launcher
  pointing at it keeps working, but a filename like `beavers_1.2.0_amd64.AppImage` would keep its
  original version number after updating. That's why the rename above to a version-free name is
  suggested. (Needs a reasonably current glibc.)

- **Arch Linux (native package)** — Beavers isn't on the AUR yet, so build the `beavers-bin`
  package yourself from the [`PKGBUILD`](arch/PKGBUILD) in this repo. It installs the same prebuilt
  release binary and uses your system WebKit:
  ```bash
  git clone https://github.com/ssbrear/beavers-dist.git
  cd beavers-dist/arch
  less PKGBUILD      # review it first, as with any PKGBUILD
  makepkg -si
  ```
  **This install does not update itself.** Package builds leave the in-app updater out, and pacman
  doesn't know where the package came from. To update, run `git pull && makepkg -si` in the same
  folder. To hear about new versions, watch this repo for releases (**Watch → Custom → Releases**).

- **Windows** — download `beavers_*-setup.exe` from [Releases](../../releases) and run it.
  Beavers is **not code-signed yet**, so Windows SmartScreen will say *“Windows protected your PC.”*
  Click **More info → Run anyway**. The app updates itself in-app after install.

- **macOS** — not supported yet.

## Verifying your download

Each release includes a `SHA256SUMS` file covering every asset. Download it into the same folder as
your download, then:

```bash
sha256sum --ignore-missing -c SHA256SUMS   # verifies whichever release files you downloaded
```

`--ignore-missing` checks only the files you actually have — `SHA256SUMS` lists all platforms, so
without it `sha256sum` reports the assets you didn't download as failures.

## Privacy

Beavers runs your combat-log analysis locally and talks to WarcraftLogs only on your behalf. The
only always-on network call is a signed update check against this repository's releases (in the
self-updating AppImage/Windows builds; package-manager installs make no such call).
