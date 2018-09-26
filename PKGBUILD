# $Id$
# Credits: Felix Yan <felixonmars@archlinux.org>

_pkgver=2.20
_pkgname=libblockdev
pkgname=libblockdev-minimal
pkgver=2.20
pkgrel=1
pkgdesc="A library for manipulating block devices"
arch=('x86_64')
url="https://github.com/rhinstaller/libblockdev"
license=('LGPL')
depends=('dosfstools' 'gptfdisk' 'libbytesize' 'parted' 'kmod' 'volume_key')
makedepends=('systemd' 'python')
provides=('libblockdev')
conflicts=('libblockdev')
source=("$_pkgname-$_pkgver.tar.gz::https://github.com/rhinstaller/libblockdev/archive/$_pkgver-1.tar.gz")
sha512sums=('4cb6b18d5de63461f35e0b6f6896599aa41da2c995839c2e88661dacdf07522842b612820fb1d83edbde72092cc62295d5411e8607f52c611db7f02aa16c9ab3')

build() {
  cd "$srcdir"/$_pkgname-$_pkgver-1
  ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/etc --without-lvm_dbus --without-dm --without-btrfs --without-lvm --disable-introspection --without-nvdimm --without-vdo 
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
