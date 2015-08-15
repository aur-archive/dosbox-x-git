# Mantainer: Franco Tortoriello

pkgname=dosbox-x-git
pkgver=957.d29bfa7
pkgrel=1
pkgdesc="x86 emulator with builtin DOS, with patches with more features"
arch=(i686 x86_64)
url="http://dosbox.sourceforge.net"
license=(GPL)
depends=(sdl_net sdl_sound libpng mesa)
makedepends=(subversion glu openglide-cvs munt-git)
provides=(dosbox dosbox-svn dosbox-svn-patched dosbox-debug bin32-dosbox bin32-dosbox-svn bin32-dosbox-svn-patched)
conflicts=(dosbox dosbox-svn dosbox-svn-patched dosbox-debug bin32-dosbox bin32-dosbox-svn bin32-dosbox-svn-patched)
source=(dosbox::git://github.com/joncampbell123/dosbox-x.git
	dosbox.png
	dosbox.desktop)

pkgver() {
  cd "$SRCDEST/dosbox"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd "$srcdir/dosbox"

  ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/etc/dosbox
  make
}

package() {
  cd "$srcdir/dosbox"
  make DESTDIR="$pkgdir" install
  install -Dm644 "$srcdir/dosbox.png" \
	"$pkgdir/usr/share/pixmaps/dosbox.png"
  install -Dm644 "$srcdir/dosbox.desktop" \
	"$pkgdir/usr/share/applications/dosbox.desktop"
}

md5sums=('SKIP'
         '3dcfe45c5ed0433316eaea51e3620b36'
         '77b693e82f9dd018d1ec763a3c60ec4f')