# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/media-player-info
# 						Maintainer : Ionut Biru <ibiru@archlinux.org>
# 						Contributor: Marti Raudsepp <marti@juffo.org>

pkgname=media-player-info
pkgver=22
pkgrel=2
pkgdesc="Data files describing media player capabilities, for post-HAL systems"
arch=('x86_64')
license=('BSD')
url="http://cgit.freedesktop.org/media-player-info/"
depends=()
makedepends=('python')
source=(http://www.freedesktop.org/software/media-player-info/${pkgname}-$pkgver.tar.gz)
sha256sums=('7ee7d7712834860533c46b16947238ef5b5d72f394fa7fb52783a15fba7b2336')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal
install=media-player-info.install

build() {
  cd ${pkgname}-$pkgver

  ./configure --prefix=/usr \
      --with-udevdir=/usr/lib/udev
  LANG="en_US.UTF-8" make
}

package() {
  cd "${pkgname}-$pkgver"
  make DESTDIR="$pkgdir" install

  install -d "$pkgdir/usr/share/licenses/${pkgname}"
  install -m644 COPYING "$pkgdir/usr/share/licenses/${pkgname}"
}
