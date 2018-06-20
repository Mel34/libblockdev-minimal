# $Id$
# Credits: Felix Yan <felixonmars@archlinux.org>

_pkgver=2.18
_pkgname=libblockdev
pkgname=libblockdev-minimal
pkgver=1.0
pkgrel=1
pkgdesc="A library for manipulating block devices"
arch=('x86_64')
url="https://github.com/rhinstaller/libblockdev"
license=('LGPL')
depends=('dosfstools' 'gptfdisk' 'libbytesize' 'parted' 'kmod')
makedepends=('systemd' 'python')
provides=('libblockdev')
conflicts=('libblockdev')
source=("$_pkgname-$_pkgver.tar.gz::https://github.com/rhinstaller/libblockdev/archive/$_pkgver-1.tar.gz")
sha512sums=('c7837b0abb7747baf8dc2a21a0a75bc5fb80693a1685ddb310bf7d606d44ea65fa4c934cff6c09c5069806dea3ee056eb53c64122ec43b5c0485cdf92fda58d5')

build() {
  cd "$srcdir"/$_pkgname-$_pkgver-1
  ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/etc --without-lvm_dbus --without-dm --without-crypto --without-btrfs --without-lvm --disable-introspection --without-nvdimm --without-vdo 
  make
}

check() {
  cd "$srcdir"/$_pkgname-$_pkgver-1
  make check
}

package() {
  cd "$srcdir"/$_pkgname-$_pkgver-1
  make DESTDIR="$pkgdir" install
}
