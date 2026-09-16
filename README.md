# aseprite-bin

This is a fork of the AUR package [aseprite-bin](https://aur.archlinux.org/packages/aseprite-bin), it was out of date, and I did some minor adjustments on how permissions are handled, and re-derived the dependency array.

## Requirements:

- https://aseprite.org/user

## Install

1. Clone this repo somewhere
1. Download the `deb` file after logging in to [aseprite.org](https://aseprite.org), store it next to the `PKGBUILD`
3. Build and install using

```sh
makepkg -Csi # Use -f if rebuilding
```


## Update version

1. Adjust `pkgver` to match new version
2. Use `updpkgsums` to update sums
3. `makepkg --printsrcinfo > .SRCINFO` to generate `.SRCINFO` for AUR

You can use this script to check the debian dependencies, and possibly adjust the `depends` array

And use `namcap` to check for errors and missing dependencies (`pacman -S namcap`)

```sh
namcap aseprite-bin-[VERSION]-x86_64.pkg.tar.zst
```

Alternatively you can use this script to check the dependencies from the deb package

```sh
tmp=$(mktemp -d)
bsdtar -xf Aseprite_[VERSION]_amd64.deb -C "$tmp"
bsdtar -xOf "$tmp"/control.tar.* ./control
```

