<div align="center">

<img src="data/icons/dev.vlinkz.NixSoftwareCenter.svg"/>

Nix Software Center
===

[![Built with Nix][builtwithnix badge]][builtwithnix]
[![License: GPLv3][GPLv3 badge]][GPLv3]
[![Chat on Matrix][matrix badge]][matrix]

A graphical app store for Nix built with [libadwaita](https://gitlab.gnome.org/GNOME/libadwaita), [GTK4](https://www.gtk.org/), and [Relm4](https://relm4.org/). Heavily inspired by [GNOME Software](https://gitlab.gnome.org/GNOME/gnome-software).

<img src="data/screenshots/frontpage-light.png#gh-light-mode-only"/>
<img src="data/screenshots/frontpage-dark.png#gh-dark-mode-only"/> 

</div>

## NixOS Installation

Head of `configuration.nix`

```nix
{ config, pkgs, lib, ... }:
let
  nixos-conf-editor = (import (pkgs.fetchFromGitHub {
    owner = "vlinkz";
    repo = "nix-software-center";
    rev = "0.0.1";
    sha256 = "0000000000000000000000000000000000000000000000000000";
  })) {};
in
```
Packages:

```nix
environment.systemPackages =
with pkgs; [
  nix-software-center
  # rest of your packages
];
```
For any other method of installation, when rebuilding you will be prompted to authenticate twice in a row by `pkexec`

## 'nix profile' installation
```bash
nix profile install github:vlinkz/nix-software-center
```

## 'nix-env' Installation

```bash
git clone https://github.com/vlinkz/nix-software-center
nix-env -f nix-software-center -i nix-software-center
```

## Single run on an flakes enabled system:
```bash
nix run github:vlinkz/nix-software-center
```

## Single run on non-flakes enabled system:
```bash
nix --extra-experimental-features "nix-command flakes" run github:vlinkz/nix-software-center
```

## Debugging

```bash
RUST_LOG=nix_software_center=trace nix-software-center
```

## Licenses

Some icons in [data/icons](data/icons/) contains assets from the [NixOS logo](https://github.com/NixOS/nixos-artwork/tree/master/logo) and are licensed under a [CC-BY license](https://creativecommons.org/licenses/by/4.0/).

Some icons in [data/icons](data/icons/) contains assets from [GNOME Software](https://gitlab.gnome.org/GNOME/gnome-software/-/tree/main/data/icons/hicolor/scalable) and are licensed under [CC0-1.0](https://creativecommons.org/publicdomain/zero/1.0/).

[builtwithnix badge]: https://img.shields.io/badge/Built%20With-Nix-41439A?style=for-the-badge&logo=nixos&logoColor=white
[builtwithnix]: https://builtwithnix.org/
[GPLv3 badge]: https://img.shields.io/badge/License-GPLv3-blue.svg?style=for-the-badge
[GPLv3]: https://opensource.org/licenses/GPL-3.0
[matrix badge]: https://img.shields.io/badge/matrix-join%20chat-0cbc8c?style=for-the-badge&logo=matrix&logoColor=white
[matrix]: https://matrix.to/#/#nixos-gui:matrix.org