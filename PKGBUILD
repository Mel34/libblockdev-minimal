# $Id$
# Credits: Felix Yan <felixonmars@archlinux.org>

_pkgver=2.17
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
sha512sums=('e882642e124100abf578699272bf1f0a2618b5eeed3ded4582f8535173238f145f3d4a2ea7dbe4b3b464d646f6e98ef0a891e7dfa7dde7e8c3322c883f7264e6')

build() {
  cd "$srcdir"/$_pkgname-$_pkgver-1
  ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/etc --without-lvm_dbus --without-dm --without-crypto --without-btrfs --without-lvm --disable-introspection --without-nvdimm
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
