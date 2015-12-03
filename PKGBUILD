pkgname=plank
pkgver=0.10.1
pkgrel=1
pkgdesc='Elegant, simple, clean dock'
arch=('x86_64')
url='https://launchpad.net/plank'
license=('GPL3')
depends=('bamf' 'libdbusmenu-gtk3' 'libgee')
makedepends=('intltool' 'vala')
install="${pkgname}.install"
source=("https://launchpad.net/${pkgname}/1.0/${pkgver}/+download/${pkgname}-${pkgver}.tar.xz")
sha256sums=('04cf4205fb7fce035bf537395fbfc3cf79aea9692fb4186345fe6a06ce2ebf36')

build() {
  cd ${pkgname}-${pkgver}

  ./configure --prefix='/usr' --sysconfdir='/etc' --disable-apport
  make
}

package() {
  cd ${pkgname}-${pkgver}

  make DESTDIR="${pkgdir}" install
}

