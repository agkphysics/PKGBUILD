# Maintainer: Aaron Keesing <agkphysics at gmail dot com>
pkgname=labelimg-git
_pkgname=labelimg
pkgver=v1.8.3.r14.g45078ac
pkgrel=1
pkgdesc="A graphical image annotation tool."
arch=('any')
url="https://github.com/tzutalin/labelImg"
license=('MIT')
provides=("$_pkgname")
conflicts=("$_pkgname")
depends=('python-lxml' 'python-pyqt5')
source=("git+https://github.com/tzutalin/labelImg.git"
        "$_pkgname.desktop"
        "$_pkgname")
sha256sums=('SKIP'
            '8fda55ba5e3360801e3f53d60fac47b880a65a1500367d517814589fafd26833'
            '0f85aa6641f3454ef1b6658b2ce4f1de93a6ddfb46f9bfc5212f474926da2ab2')

pkgver() {
  cd "labelImg"
  git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/labelImg"
  make qt5py3
}

check() {
  cd "$srcdir/labelImg"
  LC_ALL=C make testpy3
}

package() {
  # Install executable and resources
  install -Dm755 "$srcdir/$_pkgname" "$pkgdir/usr/bin/$_pkgname"
  install -Dm755 "$srcdir/labelImg/labelImg.py" "$pkgdir/usr/lib/$_pkgname/labelImg.py"

  # Install required library files
  install -dm755 "$pkgdir/usr/lib/$_pkgname/libs"
  install -Dm644 "$srcdir/labelImg/libs/"*.py "$pkgdir/usr/lib/$_pkgname/libs"

  # Install data dir
  install -dm755 "$pkgdir/usr/lib/$_pkgname/data"
  install -Dm644 "$srcdir/labelImg/data/"* "$pkgdir/usr/lib/$_pkgname/data"

  # Install icon
  install -Dm644 "$srcdir/labelImg/resources/icons/app.svg" "$pkgdir/usr/share/pixmaps/$_pkgname.svg"

  # Install menu entry
  install -Dm644 "$srcdir/$_pkgname.desktop" "$pkgdir/usr/share/applications/$_pkgname.desktop"

  # Install license
  install -Dm644 "$srcdir/labelImg/LICENSE" "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
