# Maintainer: Rob Cornish <jrmcornish AT gmail DOT com>
# Contributer: Peter Jackson <pete@peteonrails.com>
# Contributor: Mikolaj Pastuszko <deluminathor@gmail.com>
# Contributor: Andrej Gelenberg <andrej.gelenberg@udo.edu>
pkgname=brscan3
pkgver=0.2.13_1
pkgrel=3
pkgdesc="SANE drivers from Brother for brscan3 compatible models"
arch=('i686' 'x86_64')
url='http://support.brother.com/g/s/id/linux/en'
license=('GPL' 'custom:Brother')
depends=('sane' 'sed' 'libusb-compat')
install=brscan3.install

source_i686=("http://download.brother.com/welcome/dlf006644/${pkgname}-${pkgver/_/-}.i386.rpm")
md5sums_i686=('bf7b7d00c25597339ac5b87f1707cf75')

source_x86_64=("http://download.brother.com/welcome/dlf006644/${pkgname}-${pkgver/_/-}.x86_64.rpm")
md5sums_x86_64=('860ae14adb64c95310f1fa37d76437b1')

source=('brscan3.rules' 'LICENSE.html')
md5sums=('76537a0eb5b68c48b57b4409397a4fa5' 'ccffb9a6f6d436b21be25b0241068981')

package() {
  cp -r "$srcdir"/usr "$pkgdir"

  install -d -m755 "$pkgdir"/etc/udev/rules.d
  install -D -m644 "$srcdir"/brscan3.rules "$pkgdir"/etc/udev/rules.d

  install -d -m755 "$pkgdir"/usr/share/licenses/$pkgname
  install -D -m644 "$srcdir"/LICENSE.html "$pkgdir"/usr/share/licenses/$pkgname

  [ "$CARCH" = x86_64 ] && mv "$pkgdir"/usr/lib64 "$pkgdir"/usr/lib

  cd "$pkgdir"/usr/lib
  ln -sf libbrscandec3.so.1.0.0 libbrscandec3.so.1
  ln -sf libbrscandec3.so.1 libbrscandec3.so

  cd "$pkgdir"/usr/lib/sane
  ln -sf libsane-brother3.so.1.0.7 libsane-brother3.so.1
  ln -sf libsane-brother3.so.1 libsane-brother3.so
}
