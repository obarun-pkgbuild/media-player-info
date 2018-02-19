# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/media-player-info
# 						Maintainer : Ionut Biru <ibiru@archlinux.org>
# 						Contributor: Marti Raudsepp <marti@juffo.org>

pkgname=media-player-info
pkgver=23
pkgrel=2
pkgdesc="Data files describing media player capabilities, for post-HAL systems"
arch=('x86_64')
license=('BSD')
url="https://www.freedesktop.org/wiki/Software/media-player-info/"
depends=()
makedepends=('python' 'git')
_commit=1ad540c1781c4c840f74344f67340a74bd458f49  # tags/23^0
source=("git+https://anongit.freedesktop.org/git/media-player-info#commit=$_commit")
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal
install=media-player-info.install

pkgver() {
  cd $pkgname
  git describe --tags | sed 's/-/+/g'
}
prepare() {
  cd $pkgname
  NOCONFIGURE=1 ./autogen.sh
}

check() {
  cd $pkgname
  make check
}

build() {
  cd "${pkgname}"

  ./configure --prefix=/usr \
      --with-udevdir=/usr/lib/udev
  LANG="en_US.UTF-8" make
}

package() {
  cd "${pkgname}"
  make DESTDIR="$pkgdir" install

  install -d "$pkgdir/usr/share/licenses/${pkgname}"
  install -m644 COPYING "$pkgdir/usr/share/licenses/${pkgname}"
}
