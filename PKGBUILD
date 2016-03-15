pkgname=plank
pkgver=0.11.0
pkgrel=1
pkgdesc='Elegant, simple, clean dock'
arch=('x86_64')
url='https://launchpad.net/plank'
license=('GPL3')
depends=('bamf' 'libdbusmenu-gtk3' 'libgee')
makedepends=('intltool' 'vala')
install="${pkgname}.install"
source=("https://launchpad.net/${pkgname}/1.0/${pkgver}/+download/${pkgname}-${pkgver}.tar.xz"
        "planksettings.desktop")
md5sums=('5ae6d28b3f4b962611299e08af013111'
         '63c93d68e8f86c08856355d070b5c11f')

build() {
  cd ${pkgname}-${pkgver}

  ./configure --prefix='/usr' --sysconfdir='/etc' --disable-apport
  make
}

package() {
  cd ${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install
  install -m644 "${srcdir}/planksettings.desktop" \
  "${pkgdir}/usr/share/applications/"
}
