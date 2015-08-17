# Maintainer: numeral <numerical@gmail.com>
pkgname=python-pydot-hg
pkgver=r19.ac76697320d6
pkgrel=1
pkgdesc="Python interface to GraphViz's Dot language"
arch=(any)
url="https://bitbucket.org/prologic/pydot"
license=('GPL')
groups=()
depends=('graphviz' 'python-pyparsing')
makedepends=('mercurial')
provides=()
conflicts=()
replaces=()
backup=()
options=(!emptydirs)
install=
source=()
md5sums=()

_hgroot=https://bitbucket.org/prologic/pydot
_hgrepo=pydot

pkgver() {
  cd "$srcdir/$_hgrepo"
  printf "r%s.%s" "$(hg identify -n)" "$(hg identify -i)"
}

build() {
  cd "$srcdir"
  msg "Connecting to Mercurial server...."

  if [[ -d "$_hgrepo" ]]; then
    cd "$_hgrepo"
    hg pull -u
    msg "The local files are updated."
  else
    hg clone "$_hgroot" "$_hgrepo"
  fi

  msg "Mercurial checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_hgrepo-build"
  cp -r "$srcdir/$_hgrepo" "$srcdir/$_hgrepo-build"
  cd "$srcdir/$_hgrepo-build"
}



package() {
  cd "$srcdir/$_hgrepo-build"
  python setup.py install --root="$pkgdir/" --optimize=1
}



# vim:set ts=2 sw=2 et:
