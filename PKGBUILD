# Maintainer: Dani Rodríguez <dani@danirod.es>
# Contributor: Carlos Aznarán <caznaranl@uni.pe>
# Contributor: Luis Martinez <luis dot martinez at disroot dot org>
# Contributor: Bjoern Franke <bjo+aur@schafweide.org>
# Contributor: Daniel Moch <daniel AT danielmoch DOT com>
# Contributor: gue5t <gue5t@aur.archlinux.org>
_base=Mastodon.py
pkgname=python-mastodon
pkgver=2.0.0
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
source=(${_base}-${pkgver}.tar.gz::${url}/archive/${pkgver}.tar.gz)
sha512sums=('abf2d6420da989980084807417f8a92c8f50fd0bb6cdb3ddf1fc3cca5190ac181ec2c47b243943927eca9a2f073fc09f3ee2bdeeaf6a47da13e36931531b60cd')

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
