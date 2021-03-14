# Maintainer: Shatur <genaloner@gmail.com>
# Contributor: alium <alium@artixlinux.org>

pkgname=optimus-manager-qt
pkgver=1.6.0
pkgrel=1
pkgdesc='A Qt interface for Optimus Manager that allows to configure and switch GPUs on Optimus laptops using the tray menu'
arch=(x86_64)
url=https://github.com/Shatur95/optimus-manager-qt
license=(GPL3)
depends=(qt5-base qt5-svg qt5-x11extras 'optimus-manager>=1.4' 'knotifications' 'kiconthemes')
makedepends=(qt5-tools libxrandr extra-cmake-modules)
source=($pkgname-$pkgver.tar.gz::$url/archive/$pkgver.tar.gz)
sha256sums=('13e627617087845b81ca4ecd19cbbda7393d5bd823a77b7115f34fa4282991a9')

prepare() {
  cd $pkgbase-$pkgver
  mkdir -p build
}

build() {
  cd $pkgname-$pkgver/build
  cmake -D CMAKE_INSTALL_PREFIX="$pkgdir/usr" -D WITH_PLASMA=ON ..
  cmake --build .
}

package_optimus-manager-qt() {
  cd $pkgname-$pkgver/build-qt
  cmake --install .
  rm -f "${pkgdir}/usr/share/icons/hicolor/icon-theme.cache"
}
