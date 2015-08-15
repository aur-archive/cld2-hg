# Maintainer: lilydjwg <lilydjwg@gmail.com>

_pkgname=cld2
pkgname=${_pkgname}-hg
pkgver=64
pkgrel=1
pkgdesc='Compact Language Detector 2'
arch=('x86_64')
url='https://code.google.com/p/cld2/'
license=('Apache')
provides=('cld2')
source=('cld2::svn+http://cld2.googlecode.com/svn/trunk/')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"
  svnversion | tr -d [A-z]
}

build() {
  cd "$srcdir/$_pkgname"
  cd internal
  sh ./compile_libs.sh
}

package() {
  cd "$srcdir/$_pkgname"
  install -Dm755 internal/libcld2.so ${pkgdir}/usr/lib/libcld2.so
  install -Dm755 internal/libcld2_full.so ${pkgdir}/usr/lib/libcld2_full.so

  for header in internal/*.h public/*.h; do
    install -Dm644 $header ${pkgdir}/usr/include/cld2/$header
  done

  install -Dm644 LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
}

