# $Id$
# Credits: Felix Yan <felixonmars@archlinux.org>

_pkgver=2.23
_pkgname=libblockdev
pkgname=libblockdev-minimal
pkgver=$_pkgver
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
sha512sums=('e1e9976d24bdd8775310c9b25c31eb3b0e2d06a295b75f0c281def694104664f42abbbec307fbeb7c960ba5059299d0da66aa7afb26850c3640a8e73ea777aaf')

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
