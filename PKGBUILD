#Maintainer: Alex Brinister (alex_brinister@yahoo.com)
pkgname=frc-wpilib
pkgver=2013svn3623+1
pkgrel=3
pkgdesc="The WPI FIRST Robotics Competition C/C++ library for the VxWorks 6.3 GCC Toolchain"
arch=(any)
provides=('frc-wpilib')
conflicts=('frc-gcc-tools')
url="http://firstforge.wpi.edu/sf/projects/c--11_toochain"
license=('custom=FRC-BSD')
depends=()
makedepends=('gcc-powerpc-wrs-vxworks' 'frcmake')
options=('!strip' 'libtool' '!zipman')
source=("git+https://github.com/alexbrinister/wpilib.git")
#		https://www.dropbox.com/s/5exwqg6izhd2xrf/"$pkgname"_"$pkgver".orig.tar.bz2)
sha512sums=('SKIP')
#			'6ccc5fecbca1adb5ff35b5186c4e138d2021003b157f74e3109073d8331f40fad3188ca6b7f201a89ecf111dd327ce8f5f5b8fbb4734ab67f035e10289bc8c63')

_wpilib='WPILib'
_wpilib_git='wpilib'

build() {
	cd $srcdir/$_wpilib_git
	mkdir build && cd build
	cmake -DCMAKE_TOOLCHAIN_FILE="/usr/powerpc-wrs-vxworks/share/cmake/toolchain.cmake" ..
	make -j2 || return 1
	
}
package () {
	cd $srcdir/$_wpilib_git/build
	make -j2 DESTDIR="${pkgdir}" install || return 1
	install -Dm644 ../BSD_License_for_WPILib_code.txt $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
#vim:set ts=2 sw=2
