pkgname=plank
pkgver=0.11.0
pkgrel=2
pkgdesc='Elegant, simple, clean dock'
arch=('x86_64')
url='https://launchpad.net/plank'
license=('GPL3')
depends=('bamf' 'libdbusmenu-gtk3' 'libgee')
makedepends=('intltool' 'vala')
optdepends=('midna-gtk-icon-theme: gtk icon theme pack for midna)
install="${pkgname}.install"
source=("https://launchpad.net/${pkgname}/1.0/${pkgver}/+download/${pkgname}-${pkgver}.tar.xz"
        "git+https://github.com/Gabrielgtx/plank-extra-themes.git"
        "planksettings.desktop")
md5sums=('5ae6d28b3f4b962611299e08af013111'
         'SKIP'
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
  cd "../${pkgname}-extra-themes/themes-repo/Themes"
  cp -r * "${pkgdir}/usr/share/plank/themes"
}
