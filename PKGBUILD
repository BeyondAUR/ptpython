# Maintainer: Carl George < arch at cgtx dot us >
# Contributor: Erik Johnson <palehose at gmail dot com>
# Contributor: <kwrazi at gmail dot com>

pkgbase="ptpython"
pkgname="ptpython"
pkgver="3.0.13"
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
)
optdepends=(
    "ipython: ptipython (ptpython + ipython)"
)
provides=("ptpython3")
# source=("https://files.pythonhosted.org/packages/49/b7/e11d308880e24387e71eb81c2fc20e22aee573542be7cff540051334a59b/${pkgbase}-${pkgver}.tar.gz")
source=("${pkgbase}-${pkgver}.tar.gz::https://github.com/prompt-toolkit/ptpython/archive/${pkgver}.tar.gz")
sha256sums=('581bd60a7b2e123fbe36347d236c325ea58e9816abec7d3b6f59a1342c18be8b')

prepare() {
    cp -a "${srcdir}/${pkgbase}-${pkgver}" "${srcdir}/${pkgbase}2-${pkgver}"
}

build() {
    cd "${srcdir}/${pkgbase}-${pkgver}"
    python setup.py build
}

package() {
    cd "${srcdir}/${pkgbase}-${pkgver}"
    python setup.py install --skip-build --root="${pkgdir}" --optimize=1
    install -D --mode 644 --target-directory "$pkgdir/usr/share/licenses/$pkgname" LICENSE
}
