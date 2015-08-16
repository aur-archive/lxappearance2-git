# Maintainer: Ner0
# Contributor: Dave Reisner <d@falconindy.com>
# Contributor: Keshav P R <skodabenz at rocketmail dot com>
# Contributor: Isaac Aggrey <isaac.aggrey@gmail.com>

pkgname=lxappearance2-git
pkgver=0.5.5.22.g6dc8b82
pkgrel=1
pkgdesc="GTK+ theme switcher for LXDE (manages icons and fonts) - Version 2 - GIT"
arch=('i686' 'x86_64')
license=('GPL2')
url="http://lxde.org/"
groups=('lxde')
depends=('gtk2' 'intltool')
makedepends=('git' 'docbook-xsl')
conflicts=('lxappearance')
provides=("lxappearance=$pkgver")
source=('git://lxde.git.sourceforge.net/gitroot/lxde/lxappearance')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/lxappearance"
  git describe --always | sed 's|-|.|g'
}

prepare() {
  cd "$srcdir/lxappearance"

  #sed -i 's/AC_PROG_CC/AC_PROG_CC\nAM_PROG_CC_C_O/' ./configure.ac
  sed -i 's/foreign/foreign subdir-objects/' ./configure.ac
  sed -i 's/xml_purge_SOURCES=.*/xml_purge_SOURCES=xml-purge.c/' ./src/Makefile.am
}

build() {
  cd "$srcdir/lxappearance"

  autoreconf -vfi
  intltoolize -f

  ./configure --prefix=/usr --sysconfdir=/etc --enable-man
  make
}

package() {
  cd "$srcdir/lxappearance"
  make DESTDIR="$pkgdir/" install
}
