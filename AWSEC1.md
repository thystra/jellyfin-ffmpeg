# AWSEC1 for Jellyfin FFmpeg 8.1.2-5

This branch is an ArgentWolf security-hardened derivative of upstream Jellyfin FFmpeg `v8.1.2-5` for Jellyfin 12.x.

## Base

- Upstream repository: `jellyfin/jellyfin-ffmpeg`
- Upstream tag: `v8.1.2-5`
- Upstream commit: `5b16ac4eeef9559e652faac4a5907c3de6e15eb8`
- Upstream FFmpeg version: 8.1.2

FFmpeg 8.1.2 already contains the upstream fixes for CVE-2026-8461. AWSEC1 keeps the stricter policy used by the Jellyfin 10.11.x hardened image and disables the MagicYUV decoder entirely as defense in depth.

## Security change

The Debian build adds:

```text
--disable-decoder=magicyuv
```

The derivative package version is generated as `8.1.2-5+awsec1-<distribution>`.

## Architecture target

The qualification workflow builds and tests Debian Trixie packages for both:

- `amd64`
- `arm64`

Qualification requires the package metadata and Jellyfin FFmpeg version to match, the MagicYUV decoder to be absent, expected hardware-acceleration interfaces to remain available, and a real libx264 encode to succeed under the target architecture.

This branch is intended to supply hardened FFmpeg 8 packages for the Jellyfin 12.x multi-platform image line.
