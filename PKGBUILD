# Maintainer: Patryk Kowalczyk <patryk AT kowalczyk ws>
pkgname=libiscsi-git
pkgver=20140808
pkgrel=1
pkgdesc="iscsi client library and utilities "
arch=('i686' 'x86_64')
url="https://github.com/sahlberg/libiscsi"
license=('GPL' 'LGPL') 
depends=()
makedepends=()
optdepends=()
conflicts=('libiscsi')
provides=('libiscsi')
replaces=('libiscsi')
install='libiscsi.install'
_gitroot="git://github.com/sahlberg/libiscsi.git"
_gitname="libiscsi"

build() {
    cd "$srcdir"
    msg "Connecting..." 
if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
else
    git clone $_gitroot $_gitname
fi

msg "GIT checkout done or server timeout"
msg "Starting make..."
rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

#
# BUILD HERE
#
	./autogen.sh
	./configure --prefix=/usr --libdir=/usr/lib
	make
}

package() {
    	cd "$srcdir/$_gitname-build"
	make DESTDIR="$pkgdir/" install
}
	
