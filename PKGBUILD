# Maintainer: Dani Rodríguez <dani@danirod.es>
pkgname=cartero
pkgver=0.1.0
pkgrel=2
epoch=
pkgdesc="Make HTTP requests and test APIs."
arch=('x86_64')
url="https://github.com/danirod/cartero"
license=('GPL-3.0-or-later')
depends=('curl' 'glib2' 'gtk4' 'gtksourceview5' 'libadwaita' 'openssl')
makedepends=('blueprint-compiler' 'git' 'meson' 'rust')
conflicts=()
options=('!strip')
source=("$pkgname-$pkgver.tar.gz::https://github.com/danirod/cartero/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('ddaec2610a51c3c3ab6da896c7ea21d91ea7ab681267ea5fe0cfb02da65c657c')

build() {
	arch-meson "${pkgname}-${pkgver}" build --wipe
	meson compile -C build
}

check() {
	meson test -C build --print-errorlogs || :
}

package() {
	meson install -C build --destdir "$pkgdir"
}
