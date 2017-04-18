# Maintainer: Carl George < arch at cgtx dot us >
# Contributor: Erik Johnson <palehose at gmail dot com>

pkgbase="ptpython"
pkgname=("ptpython" "ptpython2")
pkgver="0.39"
pkgrel="2"
pkgdesc="Python REPL build on top of prompt_toolkit"
arch=("any")
url="https://github.com/jonathanslenders/ptpython"
license=("BSD")
makedepends=("python-setuptools" "python2-setuptools")
source=("https://files.pythonhosted.org/packages/source/${pkgbase:0:1}/$pkgbase/$pkgbase-$pkgver.tar.gz")
sha256sums=('09b2e4a110d883cdb999241ac464696225807e531506adf9bce53e8ad5c5306d')

prepare() {
    cp -a "${srcdir}/${pkgbase}-${pkgver}" "${srcdir}/${pkgbase}2-${pkgver}"
}

build() {
    cd "${srcdir}/${pkgbase}-${pkgver}"
    python setup.py build
    cd "${srcdir}/${pkgbase}2-${pkgver}"
    python2 setup.py build
}

package_ptpython() {
    depends=(
        "python-docopt"
        "python-jedi>=0.9.0"
        "python-prompt_toolkit>=1.0.14"
        "python-pygments"
    )
    optdepends=(
        "ipython: ptipython (ptpython + ipython)"
    )
    provides=("ptpython3")
    cd "${srcdir}/${pkgbase}-${pkgver}"
    python setup.py install --skip-build --root="${pkgdir}" --optimize=1
    install -D --mode 644 --target-directory "$pkgdir/usr/share/licenses/$pkgname" LICENSE
}

package_ptpython2() {
    depends=(
        "python2-docopt"
        "python2-jedi>=0.9.0"
        "python2-prompt_toolkit>=1.0.14"
        "python2-pygments"
    )
    optdepends=(
        "ipython2: ptipython2 (ptpython2 + ipython2)"
    )
    cd "${srcdir}/${pkgbase}2-${pkgver}"
    python2 setup.py install --skip-build --root="${pkgdir}" --optimize=1
    install -D --mode 644 --target-directory "$pkgdir/usr/share/licenses/$pkgname" LICENSE
    rm "${pkgdir}/usr/bin/ptpython"
    rm "${pkgdir}/usr/bin/ptipython"
}
