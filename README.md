# TraceDraw for Craft Unofficial Launcher

**An unofficial mirror** of [TraceDraw](https://github.com/igtoth/tracedraw) releases, maintained by
[YalKouassi](https://github.com/YalKouassi), so that
[Craft Unofficial Launcher](https://github.com/YalKouassi/craft-unofficial-launcher) can install
and update TraceDraw.

This repo is **not affiliated with, endorsed by or supported by Ighor Toth** (the authors of TraceDraw),
**or by ArtCraft**. Report problems with TraceDraw itself upstream at
<https://github.com/igtoth/tracedraw>; report problems with this mirror here.

## What this repo publishes

The packages in this repo's releases are **TraceDraw's own builds**, as published on
[igtoth/tracedraw's releases](https://github.com/igtoth/tracedraw/releases). Nothing is rebuilt and no program file is
changed. Each release here:

- downloads upstream's packages and verifies each one before using it;
- renames them to the launcher's `<id>-<version>-<os>-<arch>` naming and, only where the launcher
  couldn't install an archive's layout, repacks that archive (the same files with the same bytes,
  in different folders);
- adds `craft-app.json`, the icon, `SHA256SUMS.txt`, and upstream's licence files from the same tag.

The notes of each release list every file, the upstream asset it came from, its SHA-256, and
whether it was repacked, so you can compare it with upstream's release.

### For TraceDraw

Upstream's packages are **renamed** to the launcher's naming contract (`windows-x86_64` becomes
`windows-x64`, `amd64` becomes `x86_64`, `arm64` on Linux becomes `aarch64`) and otherwise
mirrored **byte for byte**. Upstream publishes no checksum file, so downloads are checked against GitHub's own asset digests.

Not mirrored: the setup `.exe` and the `.msix` (the launcher installs the portable zip), and nightly builds.

## How it runs

[`.github/workflows/bridge.yml`](.github/workflows/bridge.yml) runs every 3 hours. It uses
[craft-bridge](https://github.com/YalKouassi/craft-bridge) with [`bridge.toml`](bridge.toml) to
check upstream's latest release and mirror it if this repo doesn't have it yet. If upstream starts
publishing its own `craft-app.json`, the bridge stops publishing, and the launcher should point at
upstream directly.

Using this mirror means trusting its maintainer as well as upstream; see
[craft-bridge's Trust section](https://github.com/YalKouassi/craft-bridge#trust).

## Licences

TraceDraw is licensed by its authors under Apache-2.0 OR MIT; each release attaches upstream's licence files.
This repo's own files (the config, workflow and this README) are available under MIT OR
Apache-2.0 ([LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE)).
