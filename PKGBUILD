# $Id$
# Credits: Felix Yan <felixonmars@archlinux.org>

_pkgver=2.24
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
sha512sums=('845d329bc43585a13ce021b9a1ec52d8790b7e8fbf378bde46247598ebf3f6bbb6c34ffa6b0570dfb50218278964bcf580ffa37c2f315daf63c425b326df55f1')

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
