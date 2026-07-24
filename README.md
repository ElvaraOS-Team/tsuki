# Tsuki

[Readme in English](./README.md) | [中文文档](./README_zh.md)

> [!WARNING]
> **Tsuki** is a fork of [Paru](https://github.com/Morganamilo/paru), the feature packed AUR helper. This project extends and modifies the original Paru codebase.
> For now, Tsuki is not ready to use.

Feature packed AUR helper

## Description

Tsuki is your standard pacman wrapping AUR helper with lots of features and minimal interaction.

## Features

Tsuki adds some features that are (probably) not planned in the official version:

- If opencode exists on the system, Tsuki will invoke opencode to review PKGBUILD
- `--sudopassword <password>` allows specifying the password via the `-S` flag when invoking sudo. **This feature is designed for automated scripts; do not use it unless necessary**

## Installation

For now, Tsuki is not ready to use.

```
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/tsuki.git
cd tsuki
makepkg -si
```

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).

## General Tips

- **Man pages**: For documentation on tsuki's options and config file see `tsuki(8)` and `tsuki.conf(5)` respectively.

- **Color**: Tsuki only enables color if color is enabled in pacman. Enable `color` in your `pacman.conf`.

- **File based review**: To get a more advanced review process enable `FileManager` with your file manager of choice in `tsuki.conf`.

- **Flip search order**: To get search results to start at the bottom and go upwards, enable `BottomUp` in `tsuki.conf`.

- **Editing PKGBUILDs**: When editing PKGBUILDs, you can commit your changes to make them permanent. When the package is upgraded, `git` will try to merge your changes with upstream's.

- **PKGBUILD syntax highlighting**: You can install [`bat`](https://github.com/sharkdp/bat) to enable syntax highlighting during PKGBUILD review.

- **Tracking -git packages**: Tsuki tracks -git package by monitoring the upstream repository. Tsuki can only do this for packages that tsuki itself installed. `tsuki --gendb` will make tsuki aware of packages it did not install.

## Examples

`tsuki <target>` -- Interactively search and install `<target>`.

`tsuki` -- Alias for `tsuki -Syu`.

`tsuki -S <target>` -- Install a specific package.

`tsuki -Sua` -- Upgrade AUR packages.

`tsuki -Qua` -- Print available AUR updates.

`tsuki -G <target>` -- Download the PKGBUILD and related files of `<target>`.

`tsuki -Gp <target>` -- Print the PKGBUILD of `<target>`.

`tsuki -Gc <target>` -- Print the AUR comments  of `<target>`.

`tsuki --gendb` -- Generate the devel database for tracking `*-git` packages. This is only needed when you initially start using tsuki.

`tsuki -Bi .` -- Build and install a PKGBUILD in the current directory.


## Debugging

Tsuki is not an official tool. If tsuki can't build a package, you should first check if makepkg can successfully build the package. If it can't, then you should report the issue to the maintainer. Otherwise, it is likely an issue with tsuki and should be reported here.
