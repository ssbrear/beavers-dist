# Beavers — Downloads

This is the official **download and auto-update channel** for **Beavers**, a lightweight,
privacy-respecting local World of Warcraft combat-log analyzer and WarcraftLogs report viewer.

Beavers is **proprietary, closed-source software** — free to download and run, but not open source.
This repository hosts release binaries only; there is no source code here. See [`LICENSE`](LICENSE)
for the full terms.

> **Heads up:** until the first release is published, the [Releases](../../releases) page will be
> empty. Download links below resolve once a release goes live.

## Install

- **Arch Linux** — install `beavers-bin` from the AUR:
  ```bash
  yay -S beavers-bin      # or: paru -S beavers-bin
  ```
  Uses your system WebKit and updates with `pacman -Syu`.

- **Other Linux** — download the `.AppImage` from [Releases](../../releases), then:
  ```bash
  chmod +x beavers_*.AppImage
  ./beavers_*.AppImage
  ```
  The AppImage updates itself in-app. (Needs a reasonably current glibc; on Arch prefer the AUR
  package above.)

- **Windows** — download `beavers_*-setup.exe` from [Releases](../../releases) and run it.
  Beavers is **not code-signed yet**, so Windows SmartScreen will say *“Windows protected your PC.”*
  Click **More info → Run anyway**. The app updates itself in-app after install.

- **macOS** — not supported yet.

## Verifying your download

Each release includes a `SHA256SUMS` file. After downloading:

```bash
sha256sum -c SHA256SUMS      # run in the folder with the downloaded files
```

## Privacy

Beavers runs your combat-log analysis locally and talks to WarcraftLogs only on your behalf. The
only always-on network call is a signed update check against this repository's releases (in the
self-updating AppImage/Windows builds; package-manager installs make no such call).
