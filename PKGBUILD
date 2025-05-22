# Maintainer: Carl George < arch at cgtx dot us >
# Contributor: Erik Johnson <palehose at gmail dot com>
# Contributor: <kwrazi at gmail dot com>

pkgname="ptpython"
pkgver="3.0.30"
pkgrel="1"
pkgdesc="Python REPL build on top of prompt_toolkit"
arch=("any")
url="https://github.com/prompt-toolkit/ptpython"
license=("BSD")
makedepends=("python-setuptools" "python-build" "python-installer")
depends=(
    "python-jedi>=0.9.0"
    "python-prompt_toolkit>=3.0.43"
    "python-pygments"
    "python-appdirs"
)
optdepends=(
    "ipython: ptipython (ptpython + ipython)"
)
provides=("ptpython3")
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/prompt-toolkit/ptpython/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('d893e71d45a3f6902085aa3cc14629f5a96709ffca51706aef97db1bfb31fcaf')

# prepare() {
#     cp -a "${srcdir}/${pkgname}-${pkgver}" "${srcdir}/${pkgname}2-${pkgver}"
# }

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    python -m build -wn
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    python -m installer -d "$pkgdir" dist/*.whl
    install -D --mode 644 --target-directory "$pkgdir/usr/share/licenses/$pkgname" LICENSE
}
