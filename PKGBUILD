# Maintainer: Aaron Keesing <agkphysics at gmail dot com>
pkgname=labelimg
pkgver=1.8.1
pkgrel=1
pkgdesc="A graphical image annotation tool."
arch=('any')
url="https://github.com/tzutalin/labelImg"
license=('MIT')
depends=('python-lxml' 'python-pyqt5')
source=("labelImg-${pkgver}.tar.gz::https://github.com/tzutalin/labelImg/archive/v${pkgver}.tar.gz"
        "$pkgname.desktop"
        "$pkgname")
sha256sums=('8a4ce1c47e87e4a2043a78511db72f5f98a83a21453ffd4797c1dbbceebc56ad'
            '69bf1d7f5deddad7a2a714e055f2c8a3041fd21aa59f71fc80e0cdae2fcf7f40'
            '0f85aa6641f3454ef1b6658b2ce4f1de93a6ddfb46f9bfc5212f474926da2ab2')

build() {
  cd "$srcdir/labelImg-$pkgver"
  make qt5py3
}

check() {
  cd "$srcdir/labelImg-$pkgver"
  make testpy3
}

package() {
  # Install executable and resources
  install -Dm755 "$srcdir/$pkgname" "$pkgdir/usr/bin/$pkgname"
  install -Dm755 "$srcdir/labelImg-$pkgver/labelImg.py" "$pkgdir/usr/lib/$pkgname/labelImg.py"
  install -Dm644 "$srcdir/labelImg-$pkgver/resources.py" "$pkgdir/usr/lib/$pkgname/resources.py"

  # Install required library files
  install -Dm644 "$srcdir/labelImg-$pkgver/libs/"*.py "$pkgdir/usr/lib/$pkgname/libs"

  # Install data dir
  install -Dm644 "$srcdir/labelImg-$pkgver/data/"* "$pkgdir/usr/lib/$pkgname/data"

  # Install icon
  install -Dm644 "$srcdir/labelImg-$pkgver/resources/icons/app.svg" "$pkgdir/usr/share/pixmaps/$pkgname.svg"

  # Install menu entry
  install -Dm644 "$srcdir/$pkgname.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"

  # Install license
  install -Dm644 "$srcdir/labelImg-$pkgver/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
