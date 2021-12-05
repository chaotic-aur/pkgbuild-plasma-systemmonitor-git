# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=plasma-systemmonitor
pkgver=5.23.80_r520.g364bada
pkgrel=1
pkgdesc='An interface for monitoring system sensors, process information and other system resources'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(GPL LGPL)
depends=(ksystemstats-git kitemmodels-git qqc2-desktop-style-git kquickcharts-git)
makedepends=(extra-cmake-modules-git)
groups=(plasma-git)
source=("git+https://invent.kde.org/plasma/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
