# Maintainer: Daniel Berg <mail@roosta.sh>
#
# INFO:
# - https://aseprite.org/user
#
# 1. Add deb file from aseprite website next to this
# 2. Adjust pkgver to match new version
# 3. Use `updpkgsums` to update sums
# 4. Install using `makepkg -Cfsi`
#
# (5): Optionally check if the dependecy array has changed in the deb package
#
# This is a fork of the AUR package aseprite-bin, it was out of date, and I did
# some minor adjustments on how permissions are handled.

pkgname=aseprite-bin
pkgver=1.3.18.5
_pkgver=${pkgver}-1
pkgrel=1
pkgdesc="Create animated sprites and pixel art"
arch=('x86_64')
url="https://www.aseprite.org/"
license=('LicenseRef-Aseprite-EULA')
depends=('libx11' 'libxext' 'libxrandr' 'libglvnd' 'fontconfig' 'libxcursor' 'hicolor-icon-theme')
options=('!debug')
provides=(aseprite)
conflicts=(aseprite)
source=("local://Aseprite_${_pkgver}_amd64.deb")
sha256sums=('46d50b12d809dbd2017d571f9a342aa78b00b42f3c4e0d275438fc7cdb821c16')

package() {
    bsdtar -xf data.tar.* -C "$pkgdir" --no-same-owner

    install -d "$pkgdir/usr/share/licenses/$pkgname/"
    install -Dm644 "$pkgdir/usr/share/doc/aseprite/EULA.txt" \
        "$pkgdir/usr/share/licenses/$pkgname/EULA.txt"
    install -Dm644 "$pkgdir/usr/share/doc/aseprite/docs/LICENSES.md" \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSES.md"
}

# vim: set ts=4 sw=4 tw=0 fdm=marker et :
