![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/gaofengnan/yt-dlp-debian/total)
![GitHub Downloads (all assets, latest release)](https://img.shields.io/github/downloads/gaofengnan/yt-dlp-debian/latest/total)
![GitHub Release](https://img.shields.io/github/v/release/gaofengnan/yt-dlp-debian)
![GitHub Release Date](https://img.shields.io/github/release-date/gaofengnan/yt-dlp-debian?display_date=published_at)

<h1>
   <p align="center">
     <a href="https://github.com/yt-dlp/yt-dlp"><img src="https://github.com/gaofengnan/yt-dlp-debian/blob/main/yt-dlp-logo.png" alt="yt-dlp Logo" width="128" style="margin-right: 20px"></a>
     <a href="https://www.debian.org/"><img src="https://github.com/gaofengnan/yt-dlp-debian/blob/main/debian-logo.png" alt="Debian Logo" width="104" style="margin-left: 20px"></a>
     <br>yt-dlp for Debian
   </p>
</h1>
<p align="center">
 A feature-rich command-line audio/video downloader.
</p>

# yt-dlp for Debian

> Fork of [dariogriffo/yt-dlp-debian](https://github.com/dariogriffo/yt-dlp-debian) (MIT); the original packaging is by Dario Griffo. Served at [deb.gaofn.xyz](https://deb.gaofn.xyz) for Debian 12 (bookworm) and 13 (trixie).

This repository contains build scripts to produce the _unofficial_ Debian packages
(.deb) for [yt-dlp](https://github.com/yt-dlp/yt-dlp/) hosted at [deb.gaofn.xyz](https://deb.gaofn.xyz)

Currently supported Debian distros are:
- Bookworm (v12)
- Trixie (v13)
- Forky (v14)
- Sid (testing)

Supported architectures:
- all — yt-dlp is shipped as a self-contained Python zipapp, so a single
  `Architecture: all` package installs on amd64, arm64, armel, armhf, i386,
  ppc64el, riscv64, s390x and every other architecture.

The only runtime requirement is `python3` (>= 3.9), which every supported
release already provides. `ffmpeg` is recommended for merging and
post-processing.

This is an unofficial community project to provide a package that's easy to
install on Debian. If you're looking for the yt-dlp source code, see
[yt-dlp](https://github.com/yt-dlp/yt-dlp/).

## What's in the package

- `/usr/bin/yt-dlp` — the official upstream zipapp release
- `/usr/share/man/man1/yt-dlp.1.gz` — the man page
- bash, zsh and fish shell completions
- `/usr/share/doc/yt-dlp/` — upstream README, copyright and Debian changelog

## Install/Update

### The Debian way

```sh
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.gpg -o /etc/apt/keyrings/deb.gaofn.xyz.gpg
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.sources -o /etc/apt/sources.list.d/deb.gaofn.xyz.sources
# Debian 12 (bookworm): fetch deb.gaofn.xyz-bookworm.sources instead
sudo apt update
sudo apt install -y yt-dlp
```

### Manual Installation

1. Download the .deb package for your Debian version available on
   the [Releases](https://github.com/gaofengnan/yt-dlp-debian/releases) page.
2. Install the downloaded .deb package.

```sh
sudo dpkg -i <filename>.deb
```
## Updating

To update to a new version, just follow any of the installation methods above. There's no need to uninstall the old version; it will be updated correctly.

## Building

```sh
./build.sh <yt_dlp_version> <build_version>
# Example: ./build.sh 2026.07.04 1
```

This builds the Debian binary packages, the Ubuntu binary packages and the
source packages. Each step can also be run on its own:

```sh
./build_debian.sh 2026.07.04 1
./build_ubuntu.sh 2026.07.04 1
./build_src.sh    2026.07.04 1
```

## Roadmap

- [x] Produce a .deb package on GitHub Releases
- [x] Set up a debian mirror for easier updates
- [x] Ship the man page and shell completions
- [x] Architecture-independent package covering every architecture

## Disclaimer

- This repo is not open for issues related to yt-dlp. This repo is only for _unofficial_ Debian packaging.
