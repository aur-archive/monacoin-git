# Maintainer: kusakata <shohei atmark kusakata period com>

pkgname=monacoin-git
_gitname=monacoin
pkgver=11.106f602
pkgrel=1
pkgdesc="A peer-to-peer payment network and digital currency by 2ch"
arch=('i686' 'x86_64')
url="http://monacoin.org/"
license=('MIT')
depends=('qt4>=4.6' 'boost-libs>=1.46' 'miniupnpc>=1.6')
makedepends=('git' 'boost' 'gcc' 'make' 'automoc4')
provides=('monacoin')
install=monacoin.install
source=('git://github.com/monacoinproject/monacoin.git' 'monacoin.desktop')
md5sums=('SKIP'
         '2a8a0953bee3d1e950a0d18ab8f0934f')

pkgver() {
  cd "${_gitname}"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd "$srcdir/$_gitname"

  qmake-qt4
  make
  
  cd "$srcdir/$_gitname/src"
  make $MAKEFLAGS -f makefile.unix
}

package() {
  install -D -m755 "$srcdir/$_gitname/monacoin-qt" "$pkgdir/usr/bin/monacoin-qt"
  install -D -m755 "$srcdir/$_gitname/src/monacoind" "$pkgdir/usr/bin/monacoind"
  install -D -m644 "$srcdir/$_gitname/COPYING" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -D -m644 monacoin.desktop "$pkgdir/usr/share/applications/monacoin.desktop"
  install -D -m644 "$srcdir/$_gitname/src/qt/res/icons/bitcoin.png" "$pkgdir/usr/share/pixmaps/monacoin.png"
}
