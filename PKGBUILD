# Maintainer: Jerome Leclanche <jerome@leclan.ch>
# Contributor: Abdurrahman AVCI <abdurrahmanavci@gmail.com>

_pkgbase="sddm"
pkgname="$_pkgbase-qt5-git"
pkgver=v0.9.0
pkgrel=1
pkgdesc="QML based X11 display manager (Qt5 version from Git)"
arch=("i686" "x86_64")
url="https://github.com/sddm/sddm"
license=("GPL")
depends=("qt5-declarative" "upower")
makedepends=("git" "cmake" "qt5-tools" "python-docutils")
provides=("$_pkgbase")
conflicts=("$_pkgbase" "$_pkgbase-qt5")
replaces=("$_pkgbase" "$_pkgbase-qt5")
install="$_pkgbase.install"
backup=("usr/share/sddm/scripts/Xsetup")
source=("git://github.com/sddm/$_pkgbase.git")
sha256sums=("SKIP")

pkgver() {
	cd "$srcdir/$_pkgbase"
	git describe --always | sed "s/-/./g"
}

build() {
	cd "$srcdir"
	mkdir -p build

	cd build
	cmake ../$_pkgbase \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_INSTALL_LIBEXECDIR=/usr/lib/sddm \
		-DCMAKE_BUILD_TYPE=Release \
		-DBUILD_MAN_PAGES=ON \
		-DUSE_QT5=true
	make
}

package() {
	cd "$srcdir/build"
	make DESTDIR="$pkgdir" install
}
