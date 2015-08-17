# Maintainer: Evan Teitelman <teitelmanevan@gmail.com>

pkgname=tuxcut
pkgver=5.0
pkgrel=1
pkgdesc="Netcut-like program for Linux written in PyQt"
url="http://bitbucket.org/a_atalla/tuxcut/"
arch=('i686' 'x86_64')
license="GPL2"
depends=('python' 'pyqt' 'iproute2' 'dsniff' 'arp-scan' 'arptables')
source=(https://bitbucket.org/a_atalla/${pkgname}/downloads/tuxcut_${pkgver}_all.deb)
md5sums=('cf06438795b5671edfc97abc0302bcee')

package() {
	cd "$srcdir"
	tar xzf data.tar.gz

	# Remove hidden files
	rm -rf .??*                                
	# Remove backup files
	find . -name '*~' -type f -exec rm '{}' \;  
	sed -i '1s/python/python2/' $srcdir/opt/TuxCut/run.py
	sed -i 's/^lang =.*$/lang = "English"/' $srcdir/opt/TuxCut/run.py

	install -dm755 $pkgdir/opt/TuxCut/{ui,i18n}
	install -dm755 $pkgdir/usr/share/{applications,pixmaps,doc/tuxcut}

	install -m755 $srcdir/opt/TuxCut/run.py $pkgdir/opt/TuxCut/tuxcut
	install -m644 $srcdir/opt/TuxCut/{AboutDialog.py,pix_rc.py,TuxCut.py,pix.qrc,tuxcut.pro} $pkgdir/opt/TuxCut
	install -m644 $srcdir/opt/TuxCut/ui/* $pkgdir/opt/TuxCut/ui
	install -m644 $srcdir/opt/TuxCut/i18n/* $pkgdir/opt/TuxCut/i18n
	install -m644 $srcdir/usr/share/applications/* $pkgdir/usr/share/applications
	install -m644 $srcdir/usr/share/pixmaps/* $pkgdir/usr/share/pixmaps
	install -m644 $srcdir/usr/share/doc/tuxcut/* $pkgdir/usr/share/doc/tuxcut
}
