# Maintainer: kevku <kevku@gmx.com>
pkgname=f1lt-git
pkgver=r183.00687a9
pkgrel=1
pkgdesc="unofficial Formula 1 live timing application"
arch=('i686' 'x86_64')
url="http://f1lt.pl"
license=('GPL3')
depends=('qt4')
makedepends=('git')
conflicts=('f1lt')
source=("$pkgname::git+https://pieczar@bitbucket.org/pieczar/f1lt.git#branch=develop")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "$srcdir/$pkgname"
	sed -i 's|PREFIX = /opt/$$TARGET|PREFIX = /usr|g' F1LT.pro
	sed -i 's|SHARE=$$PREFIX/share|SHARE=$$PREFIX/share/$$TARGET|g' F1LT.pro
	qmake-qt4
	make
}

package() {
	cd "$srcdir/$pkgname"
        make INSTALL_ROOT="$pkgdir/" install
}
