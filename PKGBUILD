pkgname=plank
pkgver=0.11.1
pkgrel=1
pkgdesc='Elegant, simple, clean dock'
arch=('x86_64')
url='https://launchpad.net/plank'
license=('GPL3')
depends=('bamf' 'libdbusmenu-gtk3' 'libgee')
makedepends=('intltool' 'vala')
optdepends=('midna-theme: support GTK themes icons'
            'breeze-gtk: enhanced management for themes gtk 2 and 3')
install="${pkgname}.install"
source=("https://launchpad.net/${pkgname}/1.0/${pkgver}/+download/${pkgname}-${pkgver}.tar.xz"
        "git+https://github.com/Gabrielgtx/plank-extra-themes.git"
        "planksettings.desktop")
md5sums=('469c94df34e235b0e28f86c755666d6f'
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
