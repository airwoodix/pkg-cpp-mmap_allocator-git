# Package maintainer: airwoodix <airwoodix at posteo dot me>

pkgname=stl-mmap-allocator-git
pkgver=r116.g0eb4d80
pkgrel=1
pkgdesc="A STL allocator that mmaps files"
arch=('i686' 'x86_64')
url="https://github.com/johannesthoma/mmap_allocator"
license=('LGPL')
makedepends=('git')
source=("${pkgname%-git}::git+https://github.com/airwoodix/mmap_allocator.git#branch=fix-makefile-install-cleanup"
        "${pkgname%-git}.pc")
md5sums=('SKIP'
         '696c30059091e2acbd2aa0e7bdcc2fd6')
sha256sums=('SKIP'
            '8a2d7e6d14683f351dec9dd48fe62c6240d0e2c6676b0c3f1e75186287658e7c')

pkgver() {
    cd "${pkgname%-git}"
    printf "r%s.g%s" "$(git rev-list --count HEAD)" \
	   "$(git rev-parse --short HEAD)"
}

prepare() {
    cd "${srcdir}/${pkgname%-git}"
}

build() {
    cd "${srcdir}/${pkgname%-git}"
    make
}

package() {
    cd "${srcdir}/${pkgname%-git}"
    make DESTDIR="${pkgdir}" install
    install -D -m 644 "../${pkgname%-git}.pc" \
	    "${pkgdir}/usr/share/pkgconfig/${pkgname%-git}.pc"
}
