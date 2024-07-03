# Maintainer: Carl George < arch at cgtx dot us >
# Contributor: Erik Johnson <palehose at gmail dot com>
# Contributor: <kwrazi at gmail dot com>

pkgname="ptpython"
pkgver="3.0.27"
pkgrel="1"
pkgdesc="Python REPL build on top of prompt_toolkit"
arch=("any")
url="https://github.com/prompt-toolkit/ptpython"
license=("BSD")
makedepends=("python-setuptools")
depends=(
    "python-docopt"
    "python-jedi>=0.9.0"
    "python-prompt_toolkit>=3.0.3"
    "python-pygments"
    "python-black"
    "python-appdirs"
)
optdepends=(
    "ipython: ptipython (ptpython + ipython)"
)
provides=("ptpython3")
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/prompt-toolkit/ptpython/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('9c8110a1b6155a5cf13bea8e1ea005222cab61d7a10850a13d8c920041407972')

# prepare() {
#     cp -a "${srcdir}/${pkgname}-${pkgver}" "${srcdir}/${pkgname}2-${pkgver}"
# }

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    python setup.py build
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    python setup.py install --skip-build --root="${pkgdir}" --optimize=1
    install -D --mode 644 --target-directory "$pkgdir/usr/share/licenses/$pkgname" LICENSE
}
