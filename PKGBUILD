# Maintainer: Eric Langlois <eric@langlois.xyz>
pkgname=python-akro
_name=${pkgname#python-}
pkgver=0.0.8
pkgrel=1
pkgdesc="Spaces types for reinforcement learning"
arch=('any')
url="https://github.com/rlworkgroup/akro"
license=('MIT')
depends=(
	'python'
	'python-gym'
	'python-numpy'
)
optdepends=()
makedepends=('python-setuptools')
# Only if running pytest
# checkdepends=(
# 	'python-pytest'
# 	'python-pytest-cov'
# 	'python-pytest-xdist'
# )
source=("https://files.pythonhosted.org/packages/source/${_name::1}/$_name/$_name-$pkgver.tar.gz")
sha256sums=('4fc0dc1acf35db19b39a209e20ce14dc8197723c73d3adf3ba7f8cdc1dbf6e58')

build() {
	cd "$_name-$pkgver"
	python setup.py build
}

check() {
	cd "$_name-$pkgver/build/lib"
	# Just test that we can import it.
	# There are tests cases but many rely on tensorflow<2 or theano
	python -c "import akro"
	# pytest "$_name-$pkgver/tests"
}

package() {
	cd "$_name-$pkgver"
	python setup.py install --root="$pkgdir" --optimize=1 --skip-build
	install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
