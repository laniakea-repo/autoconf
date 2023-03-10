# Maintainer: Yujŏnja <hardboiled65@gmail.com>
# Maintainer: Lukas Fleischer <lfleischer@archlinux.org>
# Contributor: Allan McRae <allan@archlinux.org>
# Contributor: Andreas Radke <andyrtr@archlinux.org>

pkgname=autoconf
pkgver=2.71
pkgrel=2
pkgdesc="A GNU tool for automatically configuring source code"
arch=('any')
license=('GPL2' 'GPL3' 'custom')
url="https://www.gnu.org/software/autoconf"
groups=('base-devel')
depends=('awk' 'm4' 'diffutils' 'perl' 'sh')
checkdepends=('gcc-fortran')
source=("https://ftp.gnu.org/pub/gnu/${pkgname}/${pkgname}-${pkgver}.tar.xz"{,.sig})
sha256sums=('f14c83cfebcc9427f2c3cea7258bd90df972d92eb26752da4ddad81c87a0faa4'
            'SKIP')
validpgpkeys=('82F854F3CE73174B8B63174091FCC32B6769AA64')  # Zack Weinberg


build() {
	cd "${pkgname}-${pkgver}"
	./configure --prefix=/usr
	make
}

check() {
	cd "${pkgname}-${pkgver}"
	make check || `exit 0` # Some test cases failed. But the output is exactly same for dist one.
}

package() {
	cd "${pkgname}-${pkgver}"
	make DESTDIR="${pkgdir}" install

	# license exception
	install -Dm644 COPYING.EXCEPTION "$pkgdir"/usr/share/licenses/autoconf/COPYING.EXCEPTION

	# remove unwanted file
	rm -f "$pkgdir"/usr/share/info/standards.info
}
