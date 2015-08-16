# Maintainer: Glorfindel <glorfindelATsentDOTcom>
# Contributor: Yngve Inntjore Levinsen <yngveDOTinntjoreDOTlevinsenATcernDOTch>
# Contributor: Fabio Zottele <fabio . zottele @ gmail . com>
 
pkgname=kbibtex-kde4-svn
pkgver=1785
pkgrel=1
url="http://home.gna.org/kbibtex/"
pkgdesc="A BibTeX editor for KDE to edit bibliographies used with LaTeX."
license=('GPL')
depends=('kdelibs>=4.8.0' 'poppler-qt')
conflicts=('kbibtex')
provides=('kbibtex' 'kbibtex-kde4')
makedepends=('subversion' 'cmake' 'automoc4')
arch=('i686' 'x86_64')
 
source=('kbibtex::svn://svn.gna.org/svn/kbibtex/trunk/')
md5sums=('SKIP')
 
pkgver() {
  cd "$SRCDEST/kbibtex" &&  svnversion | tr -d '[A-z]'
}
 
prepare() {
    # Trick to avoid config conflict (PKGBUILD bug I think):
    cp -r "$SRCDEST/kbibtex/.svn" "$srcdir/kbibtex"
    svn revert -R kbibtex
 
    cd kbibtex
 
    install_prefix=`kde4-config --prefix`
    cmake -DCMAKE_INSTALL_PREFIX="${install_prefix}" \
      -DCMAKE_BUILD_TYPE=debugfull .
}
build() {
  cd kbibtex
 
  make || return 1
}
 
package() {
  cd kbibtex
  make DESTDIR=${pkgdir} install || return 1
}
 