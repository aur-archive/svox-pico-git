# Maintainer: Kyle <kyle@gmx.ca>
# Contributor: JoKoT3 <jokot3 at gmail dot com>
# Contributor: Christopher Brannon <chris@the-brannons.com>
pkgname=svox-pico-git
_gitname=svox
pkgver=0.0 # determined from git origin
pkgrel=2
pkgdesc="Small footprint text-to-speech engine"
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
url="https://android.googlesource.com/platform/external/svox"
license=('APACHE')
groups=()
makedepends=('git')
depends=('popt')
options=('!libtool')
source=('git+https://github.com/rhdunn/svox.git'
  'lm.patch')
md5sums=('SKIP'
         'b2f04ae31f3afe525007c3c3db5fd0ac')

pkgver() {
  cd $_gitname
  # Use the tag of the last commit
  git describe --always | sed 's/android.//g;s|-|.|g'
}

build() {
    cd $srcdir/$_gitname/pico
    patch -p2 < "$srcdir/lm.patch"
  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  cd $srcdir/$_gitname/pico
  make DESTDIR="$pkgdir/" install
} 
