# Maintainer: Andreas B. Wagner <AndreasBWagner@pointfree.net>
# Maintainer: Bhoppi Chaw <bhoppi@hotmail.com>
# Contributor: Thiago Coutinho
# Contributor: Thomas Dziedzic

pkgname=ns-3
pkgver=3.20
pkgrel=1
pkgdesc='Discrete-event network simulator to replace ns-2'
arch=('i686' 'x86_64')
url='http://www.nsnam.org/'
license=('GPL')
depends=('gsl'
'gtk2'
'libxml2'
'python2'
'sqlite3')
makedepends=('fakeroot'
'findutils')
optdepends=('openmpi: mpi support')
source=("https://www.nsnam.org/release/ns-allinone-$pkgver.tar.bz2")
md5sums=('50fd0ab33ba7006ec3eb4c8c85888bd2')

build()
{
	#_use_mpi='--enable-mpi'
	#echo '********************************'
	#echo '* To compile with mpi support, you should edit this PKGBUILD file'
	#echo '* and UNCOMMENT "_use_mpi" variable.'
	#echo '********************************'

	cd $srcdir/ns-allinone-$pkgver/

	# build ns-3
	sed -i 's/python/python2.7/g' build.py # ns-$pkgver/test.py
	grep -rl '/usr/local' . | xargs sed -i 's/\/usr\/local/\/usr/g'
	./build.py --enable-examples --enable-tests
}

package()
{
	cd $srcdir/ns-allinone-$pkgver/ns-$pkgver
	python2.7 ./waf --destdir=$pkgdir/ install
}

