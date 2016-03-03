# Maintainer: Boohbah <boohbah at gmail.com>
# Contributor: Petron <i at jingbei.li>

pkgname=opensmile
pkgver=2.2rc1
pkgrel=1
pkgdesc="A fast, real-time (audio) feature extraction utility for automatic speech, music and paralinguistic recognition research"
arch=('i686' 'x86_64')
url="http://www.audeering.com/research/opensmile"
license=('GPL')
depends=('portaudio')
options=('!makeflags')
source=("http://www.audeering.com/research-and-open-source/files/openSMILE-$pkgver.tar.gz")
md5sums=('d041c32af5e11e344a3daa7d923917cf')

build() {
  cd "openSMILE-$pkgver"
  ./autogen.sh
  ./autogen.sh
  ./configure --prefix="/usr" --with-portaudio="yes"
  make
}

package() {
  cd "openSMILE-$pkgver"
  make DESTDIR="$pkgdir" install
  mkdir -p "$pkgdir/usr/share/$pkgname"
  cp -a config "$pkgdir/usr/share/$pkgname"
}

# vim:set ts=2 sw=2 et:
