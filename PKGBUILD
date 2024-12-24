# Maintainer: Dani Rodríguez <dani@danirod.es>
pkgname=cartero
pkgver=0.1.3
pkgrel=2
epoch=
pkgdesc="Make HTTP requests and test APIs"
arch=('x86_64')
url="https://github.com/danirod/cartero"
license=('GPL-3.0-or-later')
depends=('curl' 'glib2' 'gtk4' 'gtksourceview5' 'libadwaita' 'openssl')
makedepends=('blueprint-compiler' 'git' 'meson' 'rust')
conflicts=()
options=('!lto' '!strip')
source=("$pkgname-$pkgver.tar.gz::https://github.com/danirod/cartero/releases/download/v$pkgver/cartero-$pkgver.tar.xz")
sha256sums=('3c86bed893757a4789a98f2e710fddea89893f7ac432f4062e57e5d634c5cf54')

build() {
	# To disable client side decorations in your build (and enhance the
	# integration with desktop environments others than GNOME), add the
	# following flag at the end of the next command invocation:
	# -Ddecorations=no-csd
	arch-meson "${pkgname}-${pkgver}" build --wipe
	meson compile -C build
}

check() {
	meson test -C build --print-errorlogs || :
}

package() {
	meson install -C build --destdir "$pkgdir"
}
