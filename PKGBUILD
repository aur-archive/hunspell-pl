# Contributor: Maciej Sitarz <macieks@freesco.pl>

pkgname=hunspell-pl
pkgver=20111017
pkgrel=2
pkgdesc="Polish (Poland) dictionary for Hunspell"
arch=(any)
url="http://www.sjp.pl/slownik/ort/"
license=("GPL" "LGPL" "CCPL:cc-by-sa" "MPL")
optdepends=('hunspell:	the spell checking libraries and apps')
makedepends=(rpmextract)
source=(http://download.fedora.redhat.com/pub/fedora/linux/development/rawhide/x86_64/os/Packages/${pkgname}-0.${pkgver}-1.fc17.noarch.rpm)
md5sums=('967d073599790f6b6ac0a0a3517afbbd')

build() {
	cd ${srcdir}
	rpmextract.sh ${pkgname}-0.${pkgver}-1.fc17.noarch.rpm
}

package() {
	cd "$srcdir"/usr/share

	install -dm755 ${pkgdir}/usr/share/hunspell
	install -m644 myspell/pl_PL.aff ${pkgdir}/usr/share/hunspell
	install -m644 myspell/pl_PL.dic ${pkgdir}/usr/share/hunspell

	# the symlinks
	install -dm755 ${pkgdir}/usr/share/myspell/dicts
	pushd $pkgdir/usr/share/myspell/dicts
	for file in $pkgdir/usr/share/hunspell/*; do
		ln -sv /usr/share/hunspell/$(basename $file) .
	done
	popd

	# docs
	install -dm755 ${pkgdir}/usr/share/doc/$pkgname
	install -m644 doc/${pkgname}-0.${pkgver}/README_pl_PL.txt $pkgdir/usr/share/doc/$pkgname
}
