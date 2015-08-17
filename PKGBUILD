# Maintainer: Vivien Maisonneuve <v dot maisonneuve at gmail dot com>
# Category: science
pkgname='polylib-git'
pkgver=5.22.5.r18.g8080293
pkgrel=1
pkgdesc='A library of polyhedral functions'
arch=('i686' 'x86_64')
url='http://icps.u-strasbg.fr/polylib/'
license=('GPL3')
provides=(${pkgname%-*}=$pkgver)
conflicts=(${pkgname%-*})
depends=('gmp')
makedepends=('git')
source=("$pkgname::git://repo.or.cz/polylib")
md5sums=('SKIP')

pkgver() {
    cd "$srcdir/$pkgname"
    git describe --long --tags | sed -r 's/^polylib-//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
    cd "$srcdir/$pkgname"
    autoreconf -i
    ./configure --prefix=/usr --with-libgmp
    make
}

check() {
    cd "$srcdir/$pkgname"
    make tests
}

package() {
    cd "$srcdir/$pkgname"
    make prefix="$pkgdir"/usr install
}
