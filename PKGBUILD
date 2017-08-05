# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-linux-utils
pkgver=2.4.0.0
pkgrel=1
pkgdesc="A set of tiny Linux-specific utilities"
arch=(x86_64)
url="http://skarnet.org/software/${pkgname}/"
license=('ISC')
# a temporary turn around is made here to provide s6-{reboot,poweroff,halt} by adding s6-linux-init as dependency
depends=('skalibs' 'execline' 's6' 's6-linux-init')
groups=(s6-suite)
conflicts=('s6-linux-utils-git')
source=("$pkgname::git+git://git.skarnet.org/s6-linux-utils#commit=$_commit")
_commit=14b00ac9433ab8c505060e8d6b3a6f606ffd66f9 # tag 2.4.0.0
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd ${srcdir}/${pkgname}
  ./configure --prefix=/usr \
			  --bindir=/usr/bin \
			  --sbindir=/usr/bin \
			  --datadir=/etc
  make
}

package() {
  cd ${srcdir}/${pkgname}

  DESTDIR=${pkgdir} make install
  install -D -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  
}

# vim:ft=sh ts=2 sw=2 et:
