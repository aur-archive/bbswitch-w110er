
#
# Maintainer: blackleg <blackleg@openmailbox.org>
# Based in bbswitch package

# Maintainer: Sven-Hendrik Haase <sh@lutzhaase.com>
# Contributor: M0Rf30
# Contributor: Samsagax <samsagax@gmail.com>

pkgname=bbswitch-w110er
pkgver=0.8
_extramodules=extramodules-3.17-w110er # Don't forget to update bbswitch.install
pkgrel=18
pkgdesc="Kernel module allowing to switch dedicated graphics card on Optimus laptops, linux-w110er version"
arch=('x86_64')
url=("http://github.com/Bumblebee-Project/bbswitch")
license=('GPL')
depends=('linux-w110er>=3.17' 'linux-w110er<3.18')
makedepends=('linux-w110er-headers>=3.17' 'linux-w110er-headers<3.18')
install=bbswitch-w110er.install
source=("https://github.com/Bumblebee-Project/bbswitch/archive/v${pkgver}.tar.gz")
md5sums=('5b116b31ace3604ddf9d1fc1f4bc5807')

build() {
  cd ${srcdir}/bbswitch-${pkgver}

  _kernver="$(cat /usr/lib/modules/${_extramodules}/version)"

  make KDIR=/lib/modules/${_kernver}/build
}

package() {
  cd ${srcdir}/bbswitch-${pkgver}
   
  install -Dm644 bbswitch.ko "${pkgdir}"/usr/lib/modules/${_extramodules}/bbswitch.ko
  gzip "${pkgdir}/usr/lib/modules/${_extramodules}/bbswitch.ko"
  sed -i -e "s/EXTRAMODULES='.*'/EXTRAMODULES='${_extramodules}'/" "${startdir}/bbswitch-w110er.install"                      
}
