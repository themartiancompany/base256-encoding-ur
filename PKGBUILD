# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_pkg="ethers"
pkgname="nodejs-${_pkg}"
pkgver=6.13.2
pkgrel=1
pkgdesc="A complete, compact and simple library for Ethereum and ilk, written in TypeScript."
arch=(
  # 'i686'
  # 'x86_64'
  any
)
_http="https://github.com"
_ns="ethers-io"
url="${_http}/${_ns}/${_pkg}.js"
license=(
  "MIT"
)
depends=(
  'nodejs'
)
makedepends=(
  'npm'
)
source=(
  # "https://registry.npmjs.org/${_pkg}/${_pkg}-${pkgver}.tgz"
  "${url}/archive/refs/tags/v${pkgver}.tar.gz"
  "LICENSE"
)
noextract=(
  "${_pkg}-${pkgver}.tgz"
)
sha256sums=(
  '374d48e72f1a16938b6c9b2d5fa6d1708c07685c2062024f8a47b124af7ea76c'
  '48da2f39e100d4085767e94966b43f4fa95ff6a0698fba57ed460914e35f94a0'
)

package() {
  local \
    _npmdir
  cd "${srcdir}"
  install \
    -Dm644 \
    LICENSE \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  _npmdir="${pkgdir}/usr/lib/node_modules/"
  mkdir \
    -p \
    "${_npmdir}"
  cd \
    "${_npmdir}"
  npm \
    install \
      --user \
        root \
      -g \
      --prefix \
        "${pkgdir}/usr" \
      "${srcdir}/${_pkg}-${pkgver}.tgz"
}

