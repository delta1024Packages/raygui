# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Jacob Stannix <jakestannix@gmail.com>
pkgname=raygui
pkgver=4.0
pkgrel=1
epoch=
pkgdesc="A simple and easy-to-use immediate-mode gui library"
arch=('x86_64')
url="https://github.com/raysan5/raygui"
license=('ZLIB')
groups=()
depends=("raylib>=5.0" "mesa" "xorg-server-common" )
makedepends=(gcc)
checkdepends=()
optdepends=()
provides=(raygui=4.0)
conflicts=(raygui=4.0)
replaces=()
backup=()
options=()
install=
changelog=
source=("https://github.com/raysan5/$pkgname/archive/refs/tags/$pkgver.tar.gz")
noextract=()
sha256sums=(299c8fcabda68309a60dc858741b76c32d7d0fc533cdc2539a55988cee236812)
validpgpkeys=()

prepare() {
	cd "$pkgname-$pkgver"
	cp src/raygui.h src/raygui.c
}

build() {
	cd "$pkgname-$pkgver"
	gcc -o libraygui.so src/raygui.c -shared -fpic \
		-DRAYGUI_IMPLEMENTATION \
		-lraylib \
		-lGL\
		-lm \
		-lpthread \
		-ldl \
		-lX11
}


package() {
	cd "$pkgname-$pkgver"
	install -Dm644 libraygui.so "$pkgdir/usr/lib/libraygui.so"
	install -Dm644 src/raygui.h "$pkgdir/usr/include/raygui.h"
}
