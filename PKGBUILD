# Maintainer: ToKiNoBug <tokinobug@163.com>
_pkgname=SlopeCraft
pkgname=${_pkgname}
pkgver=5.2.1
pkgrel=1
pkgdesc="Map Pixel Art Generator for Minecraft"
arch=('armv7h' 'x86_64')
url="https://github.com/SlopeCraft/SlopeCraft"
license=('GPL-3-or-later')
depends=('gcc-libs' 'glibc' 'fmt' 'libpng' 'libzip' 'zlib' 'qt6-base' 'openmp' 'ocl-icd')
makedepends=('gcc' 'cmake' 'ninja' 'eigen' 'git' 'xsimd' 'qt6-tools' 'opencl-headers' 'opencl-clhpp')
source=(SlopeCraft::git+https://github.com/SlopeCraft/SlopeCraft.git)
b2sums=('SKIP')

prepare()  {
	# git clone https://github.com/SlopeCraft/SlopeCraft.git
	cd $_pkgname
	git checkout dev
}

build() {
	cmake -S $_pkgname -B build \
		-G Ninja \
		-DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DSlopeCraft_vectorize=ON \
		-DSlopeCraft_GPU_API="OpenCL"

	cmake --build build --parallel
}

package() {
	DESTDIR="$pkgdir" cmake --install build
	
	cd "$pkgdir/usr"
	rm README.md
	rm README-en.md
	rm LICENSE
	rm LICENSE-zh.md
}
