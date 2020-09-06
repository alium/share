# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Vesa Kaihlavirta <vegai@iki.fi>
# Contributor: Mark Rosenstand <mark@borkware.net>
# Contributor: Giorgio Lando <patroclo7@gmail.com> (adjtimex patch)
# Contributor: Alexander Rødseth <rodseth@gmail.com>

pkgname=openntpd
pkgver=6.2p3
pkgrel=4.1
pkgdesc='Free, easy to use implementation of the Network Time Protocol'
url='http://www.openntpd.org/'
arch=('x86_64')
license=('BSD')
depends=('libressl')
conflicts=('ntp')
backup=('etc/ntpd.conf')
source=(https://ftp.openbsd.org/pub/OpenBSD/OpenNTPD/${pkgname}-${pkgver}.tar.gz
        openntpd.sysusers)
sha512sums=('56a04bfd8b161b365607673ac80086ff53ae943938fa49bf52edbc541432eca30730a46a4af581fe26ce3bbceb144cb25982a38959b7a3f9304c727fe60f9f50'
            'b6bb4f39eb435ce6c3314ea4a31430a1f8b70898d17d1fe07fa487bec0e79c022b004d3c11366f0f994546f454e5418caf5b3d7e6e1a205598d2bc8140417f7a')
validpgpkeys=('A1EB079B8D3EB92B4EBD3139663AF51BD5E4D8D5') # Brent Cook <bcook@openbsd.org>

prepare() {
  cd ${pkgname}-${pkgver}
  autoreconf -fiv
}

build() {
  cd ${pkgname}-${pkgver}
  CFLAGS+=' -fcommon' ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --sbindir=/usr/bin \
    --with-privsep-user=ntp \
    --localstatedir=/var 
  make
}

package() {
  cd ${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install

  rmdir "${pkgdir}/var/run"
  install -d "${pkgdir}/var/lib/ntp"
  install -Dm 644 COPYING -t "${pkgdir}/usr/share/licenses/${pkgname}"

  install -Dm 644 "${srcdir}/openntpd.sysusers" "${pkgdir}/usr/lib/sysusers.d/openntpd.conf"
}

# vim: ts=2 sw=2 et:
