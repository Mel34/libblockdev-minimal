# $Id$
# Credits: Felix Yan <felixonmars@archlinux.org>

_pkgver=2.21
_pkgname=libblockdev
pkgname=libblockdev-minimal
pkgver=2.21
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
sha512sums=('9991e5b776b4fe62b7f703753630e8ec4769c043047452d63de08d93f823b778179e4568b8b78c3963daf6219422afc9eb82bcc5b07b7f0a422162037b569e41')

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
