# Maintainer: Dani Rodríguez <dani@danirod.es>
# Contributor: Carlos Aznarán <caznaranl@uni.pe>
# Contributor: Luis Martinez <luis dot martinez at disroot dot org>
# Contributor: Bjoern Franke <bjo+aur@schafweide.org>
# Contributor: Daniel Moch <daniel AT danielmoch DOT com>
# Contributor: gue5t <gue5t@aur.archlinux.org>
_base=Mastodon.py
pkgname=python-mastodon
pkgver=2.0.1
pkgrel=1
pkgdesc="Python wrapper for the Mastodon API"
arch=(any)
url="https://github.com/halcy/${_base}"
license=(MIT)
depends=(python-requests python-dateutil python-magic python-decorator python-halcy-blurhash)
makedepends=(python-build python-installer python-setuptools python-wheel)
optdepends=('python-cryptography: webpush support'
  'python-http-ece: webpush support')
checkdepends=(python-pytest-runner python-pytest-cov python-pytest-vcr python-pytest-mock python-requests-mock python-pytz python-cryptography python-http-ece)
source=(${_base}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz)
sha512sums=('36476114e8ce9902975a12412db2eaea9c06f507a2c085a2db35c26ab15cb48589cb63ceb0cf2e86b04cdc1fbe03b678cc61ee4ba757aacdc42ba98f4a8b213a')

build() {
  cd ${_base}-${pkgver}
  python -m build --wheel --no-isolation
}

check() {
  cd ${_base}-${pkgver}
  python -m venv --system-site-packages test-env
  test-env/bin/python -m pytest
}

package() {
  cd ${_base}-${pkgver}
  PYTHONPYCACHEPREFIX="${PWD}/.cache/cpython/" python -m installer --destdir="${pkgdir}" dist/*.whl
  install -Dm 644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
