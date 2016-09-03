################################################################################
# cmocka - https://cmocka.org/
################################################################################

# Package Version/Information
pkgname=cmocka
pkgver=1.0.1
pkgrel=1
pkgdesc="cmocka is an elegant unit testing framework for C with support for mock objects."

# System Requirements
arch=('x86_64')
makedepends=('cmake>=2.8.0')

# Misc. Details
url="https://cmocka.org/"
license=('custom:Apache-2.0')
changelog=ChangeLog

# Source and Checksums
source=(
  ${url}files/1.0/${pkgname}-${pkgver}.tar.xz
  LICENSE
)
md5sums=(
  'ed861e501a21a92b2af63e466df2015e'
  'e3fc50a88d0a364313df4b21ef20c29e'
)

################################################################################
# Build/Check/Package
################################################################################

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  mkdir -p build && cd build
  cmake -DCMAKE_BUILD_TYPE=Release -DUNIT_TESTING=ON ..
  make
}

check() {
  cd "${srcdir}/${pkgname}-${pkgver}/build"
  make test
}

package(){
  cd "${srcdir}/${pkgname}-${pkgver}/build"
  make DESTDIR="${pkgdir}/" install
  install -Dm664 "${srcdir}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/Apache-2.0"
}
