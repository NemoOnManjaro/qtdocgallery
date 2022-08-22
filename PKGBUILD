_host="github.com"
_project=sailfishos
_basename=qtdocgallery

_gitname=$_basename
pkgname=$_basename

_basever=5.3.0
_gitver=4

pkgver=$_basever+git$_gitver

pkgrel=1
pkgdesc="The Glacier image gallery"
arch=('x86_64' 'aarch64')
url="https://$_host/$_project/$_gitname"
license=('LGPLv2')
optdepends=()
depends=('qt5-declarative' 'tracker3' 'tracker3-miners')
makedepends=('qt5-tools')
source=("${url}/archive/refs/tags/mer/$pkgver.tar.gz"
    '0001-workaround-missing-G_BEGIN-END_DECLS-in-tracker.patch')
sha256sums=('7f437c392789732e1cb1e940bd7560b6cc3bdf624c4513a84bf6da62fbacf9cb'
    '43e1184286366eb01c66e5d7ec4bfa01b37ca7c56d37054888a2396adb056ff3')

prepare() {
    cd ${pkgname}-mer-$_basever-git$_gitver
    touch .git
    patch -p1 --input="${srcdir}/0001-workaround-missing-G_BEGIN-END_DECLS-in-tracker.patch"
}


build() {
  cd ${pkgname}-mer-$_basever-git$_gitver
  qmake-qt5 tracker_enabled=yes MODULE_VERSION=5.0.0
  make -j1
}

package() {
  cd ${pkgname}-mer-$_basever-git$_gitver
  make -j 1 INSTALL_ROOT="${pkgdir}" install
}
