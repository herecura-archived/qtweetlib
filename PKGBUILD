# Maintainer: Kuba Serafinowski <zizzfizzix(at)gmail(dot)com>

##############################################################
#### The section below can be adjusted to suit your needs ####
##############################################################

# What type of build do you want?
# See http://techbase.kde.org/Development/CMake/Addons_for_KDE#Buildtypes to check what is supported.
# Default is RelWithDebInfo to help with debugging.

_buildtype="RelWithDebInfo"

##############################################################

pkgname=qtweetlib
pkgver=0.5
pkgrel=1
pkgdesc="C++ Qt based Twitter library"
arch=('i686' 'x86_64')
url="https://github.com/minimoog/QTweetLib"
license=('GPL2')
depends=('qjson')
makedepends=('cmake')
provides=('qtweetlib')
conflicts=('qtweetlib-git')
options=(!strip)
source=(https://github.com/downloads/minimoog/QTweetLib/QTweetLib-${pkgver}.tar.gz)
md5sums=('bf1a7cf45eb63479bf5d81d807b0d518')

# Clean options array to strip pkg if release buildtype is chosen
if [[ ${_buildtype} == "Release" ]] || [[ ${_buildtype} == "release" ]]; then
  options=()
fi

build(){
  msg "Starting build..."

  if [[ -e ${srcdir}/${pkgname}-${pkgver}-build ]]; then rm -rf ${srcdir}/${pkgname}-${pkgver}-build; fi
  mv ${srcdir}/QTweetLib-${pkgver} ${srcdir}/${pkgname}-${pkgver}
  mkdir ${srcdir}/${pkgname}-${pkgver}-build
  cd ${srcdir}/${pkgname}-${pkgver}-build

  cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=${_buildtype} ../${pkgname}-${pkgver}
  make
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}-build
  make DESTDIR=${pkgdir} install
}
