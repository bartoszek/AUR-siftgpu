# Contributor: josedavim <josedtascon@gmail.com>
# Maintainer: Danilo Bargen <mail at dbrgn dot ch>
pkgname=siftgpu
pkgver=0.5.400
pkgrel=8
pkgdesc="Sift Features over GPU using GLSL or CUDA"
arch=('i686' 'x86_64')
url="http://ccwu.me/"
license=('custom')
depends=('glew>=1.8' 'freeglut>=2.7' 'devil>=1.7')
optdepends=('opencl-nvidia')
makedepends=('git' 'cuda')
source=("${pkgname}::git+https://github.com/pitzer/SiftGPU"
        'makefile-cuda.patch'
#       'cmake-glew-pkg-config.patch'
#       'cmake-shared-lib.patch'
)
sha256sums=('SKIP'
            '5d5cd327bf156f91f81ea6ce3d5d2a7ab99f8e1df705007ac6126fb75c13cbdb')


prepare() {
  cd ${srcdir}/${pkgname}
  git apply ${srcdir}/makefile-cuda.patch
# git apply ${srcdir}/cmake-glew-pkg-config.patch
# git apply ${srcdir}/cmake-shared-lib.patch
# sed -i 's:g++:g++-5:' makefile
}

build() {
  cd ${srcdir}/${pkgname}
# mkdir -p build
# cd build
# cmake -DCMAKE_INSTALL_PREFIX=/usr -DSIFTGPU_ENABLE_CUDA=TRUE -DSIFTGPU_ENABLE_OPENCL=TRUE ${srcdir}/${pkgname}
  make -j1
}

package ()
{
  cd ${srcdir}/${pkgname}
  install -Dm755 -t ${pkgdir}/usr/lib ./bin/libsiftgpu.so 
  install -Dm755 -t ${pkgdir}/usr/include ./src/SiftGPU/SiftGPU.h
# cd build
# make install DESTDIR=${pkgdir}
  install -Dm644 ./license.txt "${pkgdir}/usr/share/licenses/${pkgname}/license.txt"
}

# vim:set ts=2 sw=2 et:
