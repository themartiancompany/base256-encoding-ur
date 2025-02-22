# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_os="$( \
  uname \
    -o)"
_source="npm"
_node="nodejs"
_pkg="base256-encoding"
pkgname="${_pkg}"
pkgver=2.0.2
pkgrel=1
pkgdesc="Base256 encoding, a.k.a. latin1 encoding"
arch=(
  # 'i686'
  # 'x86_64'
  'any'
)
_http="https://github.com"
_ns="fabiospampinato"
url="${_http}/${_ns}/${_pkg}"
license=(
  "MIT"
)
depends=(
  'nodejs'
)
if [[ "${_os}" == "GNU/Linux" ]]; then
  depends+=(
    'bdf-unifont'
  )
fi
makedepends=(
  'npm'
)
provides=(
  "${_node}-${_pkg}=${pkgver}"
)
conflicts=(
  "${_node}-${_pkg}"
)
_npm="https://registry.npmjs.org"
if [[ "${_source}" == "npm" ]]; then
  _src="${_npm}/${_pkg}/-/${_pkg}-${pkgver}.tgz"
  _sum='cd64198610e6f4f8fe20ce9811f18f11fb91dc39c711dee15783f1503c7b8b41'
elif [[ "${_source}" == "github" ]]; then
  _src="${url}/archive/refs/tags/v${pkgver}.tar.gz"
  _sum="ciao"
fi
source=(
  "${_src}"
  "LICENSE"
)
noextract=(
  "${_pkg}-${pkgver}.tgz"
)
sha256sums=(
  "${_sum}"
  '48da2f39e100d4085767e94966b43f4fa95ff6a0698fba57ed460914e35f94a0'
)

package() {
  local \
    _npmdir \
    _npm_opts=()
  _npm_opts=(
    # --user
    #   root
    -g
    --prefix
      "${pkgdir}/usr"
  )
  cd \
    "${srcdir}"
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
      "${_npm_opts[@]}" \
      "${srcdir}/${_pkg}-${pkgver}.tgz"
      # "${srcdir}/${_pkg}.js-${pkgver}"
}

