# Maintainer: jchamplin <jake.champlin.27@gmail.com>
# Based on goffice from [extra]

pkgname=goffice0.8-light
_pkgname=goffice
pkgver=0.8.17
pkgrel=3
pkgdesc="A library of document-centric objects and utilities"
arch=('i686' 'x86_64')
url="http://www.gnome.org"
license=('GPL')
options=('!libtool')
depends=('gtk2' 'libgsf')
makedepends=('intltool' 'gtk-doc')
conflicts=('goffice0.8')
provides=('goffice0.8')
source=(http://ftp.gnome.org/pub/gnome/sources/${_pkgname}/${pkgver%.*}/${_pkgname}-${pkgver}.tar.xz
        use-apiver-for-dirs.patch goffice-0.8.17-no-pcre.patch)
md5sums=('e2bc2d2f51220d6883f0797d74c385b8'
         '08541e72f497ce02fee774a3ccae2dce'
         'bf54fa8b063b79b857e5b572e94a162a')

build() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  patch -Np0 -i "${srcdir}/use-apiver-for-dirs.patch"
  patch -Np1 -i "${srcdir}/goffice-0.8.17-no-pcre.patch"
  autoreconf
  libtoolize
  ./configure --prefix=/usr --sysconfdir=/etc \
              --localstatedir=/var --disable-static \
              --with-config-backend=keyfile
  make
}

package() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
}
