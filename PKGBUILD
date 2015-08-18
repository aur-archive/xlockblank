pkgname=xlockblank
pkgver=5.41
pkgrel=1
pkgdesc="screen saver / locker for the X Window System - only includes the blank mode"
arch=(i686 x86_64)
license=('BSD')
depends=( pam libxmu)
makedepends=()
conflicts=(xlockmore)
url="http://www.tux.org/~bagleyd/xlockmore.html"
options=('!makeflags')
source=(http://www.tux.org/~bagleyd/xlock/xlockmore-$pkgver/xlockmore-$pkgver.tar.bz2
	LICENSE)
md5sums=('a9af1cc72f0fd096ba4bba9097f9291c'
         'a64afab4283f53972a6702c2e59850d7')

build() {
  cd $srcdir/xlockmore-$pkgver
  ./configure --prefix=/usr --disable-setuid \
	      --enable-appdefaultdir=/usr/share/X11/app-defaults \
	      --enable-pam --without-gtk2 --enable-blank-only --without-magick --without-mesa --without-opengl --without-xpm --without-motif --without-freetype --without-esound --without-ftgl --without-xinerama
  make
  make xapploaddir=$pkgdir/usr/share/X11/app-defaults \
       mandir=$pkgdir/usr/man/man1 \
       prefix=$pkgdir/usr install
  install -D -m644 ../LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
  mv $pkgdir/usr/man $pkgdir/usr/share/
}
