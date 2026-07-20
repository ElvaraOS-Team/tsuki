# Pinky

> [!WARNING]
> **Pinky** is a fork of [Paru](https://github.com/Morganamilo/paru), the feature packed AUR helper. This project extends and modifies the original Paru codebase.
> For now, Pinky is not ready to use.

Feature packed AUR helper

## Description

Pinky is your standard pacman wrapping AUR helper with lots of features and minimal interaction.

## Installation

For now, Pinky is not ready to use.

```
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/pinky.git
cd pinky
makepkg -si
```

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).

## General Tips

- **Man pages**: For documentation on pinky's options and config file see `pinky(8)` and `pinky.conf(5)` respectively.

- **Color**: Pinky only enables color if color is enabled in pacman. Enable `color` in your `pacman.conf`.

- **File based review**: To get a more advanced review process enable `FileManager` with your file manager of choice in `pinky.conf`.

- **Flip search order**: To get search results to start at the bottom and go upwards, enable `BottomUp` in `pinky.conf`.

- **Editing PKGBUILDs**: When editing PKGBUILDs, you can commit your changes to make them permanent. When the package is upgraded, `git` will try to merge your changes with upstream's.

- **PKGBUILD syntax highlighting**: You can install [`bat`](https://github.com/sharkdp/bat) to enable syntax highlighting during PKGBUILD review.

- **Tracking -git packages**: Pinky tracks -git package by monitoring the upstream repository. Pinky can only do this for packages that pinky itself installed. `pinky --gendb` will make pinky aware of packages it did not install.

## Examples

`pinky <target>` -- Interactively search and install `<target>`.

`pinky` -- Alias for `pinky -Syu`.

`pinky -S <target>` -- Install a specific package.

`pinky -Sua` -- Upgrade AUR packages.

`pinky -Qua` -- Print available AUR updates.

`pinky -G <target>` -- Download the PKGBUILD and related files of `<target>`.

`pinky -Gp <target>` -- Print the PKGBUILD of `<target>`.

`pinky -Gc <target>` -- Print the AUR comments  of `<target>`.

`pinky --gendb` -- Generate the devel database for tracking `*-git` packages. This is only needed when you initially start using pinky.

`pinky -Bi .` -- Build and install a PKGBUILD in the current directory.


## Debugging

Pinky is not an official tool. If pinky can't build a package, you should first check if makepkg can successfully build the package. If it can't, then you should report the issue to the maintainer. Otherwise, it is likely an issue with pinky and should be reported here.
