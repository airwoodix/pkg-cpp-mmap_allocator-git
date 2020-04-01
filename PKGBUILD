# Package maintainer: airwoodix <airwoodix at posteo dot me>

pkgname=stl-mmap-allocator
pkgver=r113.g6081a92
pkgrel=1
pkgdesc="A STL allocator that mmaps files"
arch=('i686' 'x86_64')
url="https://github.com/johannesthoma/mmap_allocator"
license=('LGPL')
makedepends=('git')
source=("${pkgname%-git}::git+https://github.com/johannesthoma/mmap_allocator.git#commit=6081a92a3b0f36156b5102f7c7071b2b6da1afe0"
        'stl-mmap-allocator.pc')
md5sums=('SKIP'
         '217274499a64db267f92e1e47a4ec7f7')
sha256sums=('SKIP'
            '1f95dd1134920c862c48dd680524fbea91c3450e29cbcfe6e120bfaf8ef800fb')

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
    mkdir -p "${pkgdir}/usr/lib" "${pkgdir}/usr/include"
    make PREFIX="${pkgdir}/usr" install
    install -D -m 644 "../stl-mmap-allocator.pc" \
	    "${pkgdir}/usr/share/pkgconfig/stl-mmap-allocator.pc"
}
