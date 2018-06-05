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
optdepends=('cuda')
makedepends=(git)
source=("${pkgname}::git+https://github.com/pitzer/SiftGPU"
        'makefile-cuda.patch')
sha256sums=('SKIP'
            'fc9325f3692589318133538b6301e645003737894723abacc431b1105c221773')


prepare() {
  cd ${srcdir}/${pkgname}
  git apply ${srcdir}/makefile-cuda.patch
  #sed -i 's:g++:g++-5:' makefile
}

build() {
  cd ${srcdir}/${pkgname}
  #mkdir -p build
  #cd build
  #cmake -DSIFTGPU_ENABLE_CUDA=TRUE -DSIFTGPU_ENABLE_OPENCL=TRUE -DBUILD_SHARED_LIBS=TRUE ../${pkgname}
  make -j1
}

package ()
{
  cd ${srcdir}/${pkgname}
  install -Dm755 -t ${pkgdir}/usr/lib ./bin/libsiftgpu.so 
  install -Dm755 -t ${pkgdir}/usr/include ./src/SiftGPU/SiftGPU.h
  install -Dm644 ./license.txt "${pkgdir}/usr/share/licenses/${pkgname}/license.txt"
}

# vim:set ts=2 sw=2 et:
