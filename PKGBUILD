# Maintainer: tocic <tocic at protonmail dot ch>

pkgname=nanobench
pkgver=4.3.7.12.g92d1822
pkgrel=1
pkgdesc="Simple, fast, accurate single-header microbenchmarking functionality for C++11/14/17/20"
arch=("x86_64")
url="https://nanobench.ankerl.com"
license=("MIT")
makedepends=('cmake' 'git')
source=('git+https://github.com/martinus/nanobench')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/nanobench"
  git describe --always --tags | sed -e 's|^v||' -e 's|-|.|g'
}

build() {
  cmake -B "build/" -S "${pkgname}" \
    -D CMAKE_BUILD_TYPE:STRING="None" \
    -D CMAKE_INSTALL_PREFIX:PATH="/usr/" \
    -Wno-dev

  cmake --build "build/"
}

package() {
  DESTDIR="${pkgdir}" cmake --install "build/"

  install -D --target-directory="${pkgdir}/usr/share/licenses/${pkgname}/" \
    --mode=644 \
    "${pkgname}/LICENSE"
}
