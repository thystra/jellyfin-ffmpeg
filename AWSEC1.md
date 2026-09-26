# Jellyfin FFmpeg 7.1.4-3 awsec1

This branch carries a minimal security hardening change on top of
Jellyfin FFmpeg v7.1.4-3.

## Security change

The MagicYUV decoder is disabled at build time:

    --disable-decoder=magicyuv

This mitigates CVE-2026-8461 while retaining Jellyfin's FFmpeg 7.1
integration.

## Source

Upstream base:

    v7.1.4-3

Hardened release:

    v7.1.4-3-awsec1

Hardened release commit:

    706d525defa40b4c3359a9059b63d035a56bf06a

## Package

Expected runtime package:

    jellyfin-ffmpeg7_7.1.4-3+awsec1-trixie_amd64.deb

The first manually qualified release package has SHA256:

    625065a539e3209717a977e9aede107bf61c4e0fc16ba78b54dea12f8ac0329b

## Qualification

Builds are checked for:

- package name, version, and architecture;
- FFmpeg 7.1.4-Jellyfin;
- absence of the MagicYUV decoder;
- CUDA support;
- VAAPI support;
- QSV support;
- DRM support;
- OpenCL support;
- Vulkan support;
- successful libx264 encoding.

Production qualification additionally confirmed successful Jellyfin
10.11.11 HLS playback and H.264/AAC transcoding.
