# Maintainer: Boohbah <boohbah at gmail.com>
# Contributor: Petron <i at jingbei.li>
# Contributor: jzombi <jzombi at gmail.com>

pkgname=opensmile
pkgver=2.3.0
pkgrel=1
pkgdesc="A fast, real-time (audio) feature extraction utility for automatic speech, music and paralinguistic recognition research"
arch=('i686' 'x86_64' 'armv7h')
url="http://www.audeering.com/research/opensmile"
license=('custom')
depends=('portaudio')
source=("$pkgname.tar.gz::http://www.audeering.com/download/opensmile-2-3-0-tar-gz/?wpdmdl=4782"
        "makefile.patch"
        "fix_conversion.patch")
sha256sums=('41adf2886089b76c000b74a479ac32ed983fc09bd81d1e9df4b0f4999ee71c7f'
            '3f7f6b1f3dada7257c8d3c52f96851c44d05d38e9e2f85f3cfd114fba5d30fb5'
            '773f3de249579084c1a6f241a687782ee36777bc909b0371624d6cb29b0a1516')

prepare() {
  cd "opensmile-$pkgver"
  patch -p 1 < $srcdir/makefile.patch
  patch -p 1 < $srcdir/fix_conversion.patch
}

build() {
  cd "opensmile-$pkgver"
  ./autogen.sh
  ./autogen.sh
  ./configure \
    --prefix="/usr" --with-portaudio="yes"
  make
}

package() {
  cd "opensmile-$pkgver"
  make DESTDIR="$pkgdir" install
  mkdir -p "$pkgdir/usr/share/$pkgname"
  cp -a config "$pkgdir/usr/share/$pkgname"
  find "$pkgdir/usr/share/$pkgname/config" -type d -exec chmod a+rx {} \;
  find "$pkgdir/usr/share/$pkgname/config" -type f -exec chmod a+r {} \;
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/LICENSE.txt"
}

# vim:set ts=2 sw=2 et:
