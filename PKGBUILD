# $Id$
# Credits: Felix Yan <felixonmars@archlinux.org>

_pkgver=2.22
_pkgname=libblockdev
pkgname=libblockdev-minimal
pkgver=2.22
pkgrel=1
pkgdesc="A library for manipulating block devices"
arch=('x86_64')
url="https://github.com/rhinstaller/libblockdev"
license=('LGPL')
depends=('dosfstools' 'gptfdisk' 'libbytesize' 'parted' 'kmod' 'volume_key')
makedepends=('autoconf-archive' 'gobject-introspection' 'systemd' 'python')
provides=('libblockdev')
conflicts=('libblockdev')
source=("$_pkgname-$_pkgver.tar.gz::https://github.com/rhinstaller/libblockdev/archive/$_pkgver-1.tar.gz")
sha512sums=('43a826ad4d3fb350b251063d4a90108306bdfa5279db739fb7cab0cacaf5f958c68fe5f95d12d29e17ad9b391bcaa3ceebbf67cd3ae6edcc0e0a982a35cd6ba3')

build() {
  cd "$srcdir"/$_pkgname-$_pkgver-1
  ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/etc --without-lvm_dbus --without-dm --without-btrfs --without-lvm --disable-introspection --without-nvdimm --without-vdo --without-tools
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
