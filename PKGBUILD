pkgname=qt5-feedback-git
pkgver=v5.0.0.beta1.r21.g862de79
pkgrel=2
pkgdesc='A cross-platform application and UI framework (QtFeedback)'
groups=('qt' 'qt5')
arch=('i686' 'x86_64')
url="http://qt-project.org/"
license=('GPL3' 'LGPL')
depends=('qt5-base' 'qt5-declarative')
makedepends=('git')
replaces=('qt5-qtfeedback-git')
conflicts=('qt5-feedback')
provides=('qt5-feedback')
options=('!libtool')
_gitroot="git://code.qt.io/qt/qtfeedback.git"
_gitname="qt5-feedback"
source=(${_gitname}::${_gitroot})
md5sums=('SKIP')

pkgver() {
	cd ${srcdir}/${_gitname}
    ( set -o pipefail
      git describe --long --tags 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
      printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
    )
}

build() {
	cd ${srcdir}/${_gitname}
	qmake
	make
}

package() {
	cd ${srcdir}/${_gitname}
	make INSTALL_ROOT="${pkgdir}" install
}
