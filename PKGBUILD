# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Frederik Schwan <freswa at archlinux dot org>
# Contributor: Hao Long <imlonghao@archlinuxcn.org>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_py="python"
_pkg="rich"
pkgbase="${_py}-${_pkg}"
pkgname=(
  "${pkgbase}"
)
pkgver=13.7.0
pkgrel=1
_pkgdesc=(
  'Render rich text, tables, progress bars,'
  'syntax highlighting, markdown and more to the terminal'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_ns="willmcgugan"
_http="https://github.com"
url="${_http}/${_ns}/${_pkg}"
license=('MIT')
depends=(
  "${_py}-"{colorama,markdown-it-py,pygments}
)
makedepends=(
  "${_py}-"{build,installer,poetry-core,wheel}
)
provides=(
  "${_pkg}=${pkgver}"
)
conflicts=(
  "${_pkg}"
)
source=(
  "${url}/archive/v${pkgver}/${_pkg}-${pkgver}.tar.gz"
)
b2sums=(
  'd474b5817c0e64143313a1d0b66ef0953990196ecef6b0fd62d82828902008fa7293290c7f43c605a0c897ecebecb84e816583da8921cd31fc56c902ead2f5c9'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  python \
    -m \
      build \
    --wheel \
    --no-isolation
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
      --destdir="${pkgdir}" \
      dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    "${pkgdir}"/usr/share/licenses/${pkgname}/LICENSE
}

# vim:set sw=2 sts=-1 et:
