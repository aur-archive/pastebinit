#Maintainer: Francois Boulogne <fboulogne at april dot org>

pkgname=pastebinit
pkgver=1.3.1
pkgrel=2
pkgdesc="Send anything you want directly to a pastebin from the command line"
arch=('any')
url="http://launchpad.net/pastebinit"
license=("GPL")
depends=("python2" "python2-configobj" )
makedepends=("asciidoc")
source=(http://launchpad.net/pastebinit/trunk/${pkgver}/+download/${pkgname}-${pkgver}.tar.gz) 
md5sums=('ebe0f8f118519d3505eabe0f48a10ad5')

build() {
	cd "${srcdir}/${pkgname}-${pkgver}"
	install -d "$pkgdir"/usr/{bin,share/man/man1,share/locale} "$pkgdir"/etc
	#python 2
	sed -i -e "s|#!/usr/bin/env python$|#!/usr/bin/env python2|" pastebinit
	install -m 755 pastebinit "$pkgdir"/usr/bin
	cp -a pastebin.d "$pkgdir"/usr/share
	a2x -f manpage pastebinit.xml
	install -m 644 pastebinit.1 "$pkgdir"/usr/share/man/man1
	cd po
	make
	cp -a mo/* "$pkgdir"/usr/share/locale
}
