pkgname=plank
pkgver=0.11.4
pkgrel=1
pkgdesc='Elegant, simple, clean dock'
arch=('x86_64')
url='https://launchpad.net/plank'
license=('GPL3')
depends=('bamf' 'libdbusmenu-gtk3' 'libgee>=0.20.0')
makedepends=('intltool' 'vala')
optdepends=('midna-themes: support GTK themes icons'
            'gtk-theme-arc-git: enhanced management for themes gtk 2 and 3 with support transparent elements')
install="${pkgname}.install"
source=("https://launchpad.net/plank/1.0/${pkgver}/+download/${pkgname}-${pkgver}.tar.xz"
        "git+https://github.com/Gabrielgtx/plank-extra-themes.git"
        "planksettings.desktop")
md5sums=('d2405f33bfefd16ab80c868f83526f9b'
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
