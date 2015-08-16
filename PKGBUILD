# Maintainer: Pier Luigi Fiorini <pierluigi.fiorini@gmail.com>

pkgname=kpackage-git
pkgver=r131.047c15f
pkgrel=1
pkgdesc="Framework that lets applications manage user installable packages of non-binary assets"
arch=("i686" "x86_64")
url="https://projects.kde.org/projects/frameworks/kpackage"
license=("LGPL")
depends=("qt5-base" "karchive" "ki18n" "kcoreaddons" "kconfig")
makedepends=("extra-cmake-modules" "git" "qt5-tools" "python" "kdoctools")
groups=("kf5")
conflicts=("kpackage")
provides=("kpackage")
source=("git://anongit.kde.org/kpackage.git")
md5sums=("SKIP")

pkgver() {
  cd kpackage
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../kpackage \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
