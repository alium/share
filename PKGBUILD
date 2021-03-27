pkgname=solo-python
pkgver=0.0.27
pkgrel=2
pkgdesc="Tools and Python library for SoloKeys."
arch=('any')
url="https://github.com/solokeys/solo-python"
license=('Apache' 'MIT')
depends=('python' 'python-click>=7.0' 'python-cryptography' 'python-ecdsa'
         'python-fido2' 'python-intelhex' 'python-pyserial' 'python-pyusb'
         'python-requests')
makedepends=('fakeroot' 'python-setuptools')
source=("https://files.pythonhosted.org/packages/source/s/${pkgname}/${pkgname}-${pkgver}.tar.gz"
	"https://raw.githubusercontent.com/alium/share/master/solo")
sha256sums=('72a4699eb3b1979d7a2561c538987f868b5e7ee4e4a5b402b8a4d460d3dd6ec7'
            'd4206872009b63693fc0eeec7c82096bff06b58cc938523f1820f46f071a5642')

build() {
  cd $pkgname-$pkgver
  python setup.py build
}

package() {
  cd $pkgname-$pkgver
    python setup.py install --root="${pkgdir}" --optimize=1
  install -m755 -d "${pkgdir}/usr/bin"
  install -m755  "${srcdir}"/solo "${pkgdir}/usr/bin"
}
