# Maintainer: Aaron Keesing <agkphysics at gmail dot com>
pkgname=labelimg
pkgver=1.8.3
pkgrel=1
pkgdesc="A graphical image annotation tool."
arch=('any')
url="https://github.com/tzutalin/labelImg"
license=('MIT')
depends=('python-lxml' 'python-pyqt5')
source=("labelImg-${pkgver}.tar.gz::https://github.com/tzutalin/labelImg/archive/v${pkgver}.tar.gz"
        "$pkgname.desktop"
        "$pkgname"
        "0001-fix-version-import.patch")
sha256sums=('13e5a7bedebf0e3474b36fdc8322af1845cd3e8b4d03f99e55e993a3d7876ef5'
            '8fda55ba5e3360801e3f53d60fac47b880a65a1500367d517814589fafd26833'
            '0f85aa6641f3454ef1b6658b2ce4f1de93a6ddfb46f9bfc5212f474926da2ab2'
            'ed20755134785773ea7fdfdbf393216f215295980a1960f8096cb9bde6a224bb')

prepare() {
  cd "$srcdir/labelImg-$pkgver"
  patch -Np1 <"$srcdir/0001-fix-version-import.patch"
}

build() {
  cd "$srcdir/labelImg-$pkgver"
  make qt5py3
}

check() {
  cd "$srcdir/labelImg-$pkgver"
  LC_ALL=C make testpy3
}

package() {
  # Install executable and resources
  install -Dm755 "$srcdir/$pkgname" "$pkgdir/usr/bin/$pkgname"
  install -Dm755 "$srcdir/labelImg-$pkgver/labelImg.py" "$pkgdir/usr/lib/$pkgname/labelImg.py"

  # Install required library files
  install -dm755 "$pkgdir/usr/lib/$pkgname/libs"
  install -Dm644 "$srcdir/labelImg-$pkgver/libs/"*.py "$pkgdir/usr/lib/$pkgname/libs"

  # Install data dir
  install -dm755 "$pkgdir/usr/lib/$pkgname/data"
  install -Dm644 "$srcdir/labelImg-$pkgver/data/"* "$pkgdir/usr/lib/$pkgname/data"

  # Install icon
  install -Dm644 "$srcdir/labelImg-$pkgver/resources/icons/app.svg" "$pkgdir/usr/share/pixmaps/$pkgname.svg"

  # Install menu entry
  install -Dm644 "$srcdir/$pkgname.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"

  # Install license
  install -Dm644 "$srcdir/labelImg-$pkgver/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
