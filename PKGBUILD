# Contributor: Tom K <tomk@runbox.com>
# Contributor: kastor <kastor@fobos.org.ar>

pkgname=amap
pkgver=5.2
pkgrel=4
pkgdesc="Next-generation tool for assisting network penetration testing."
depends=('glibc' 'pcre' 'openssl')
source=(http://freeworld.thc.org/releases/$pkgname-$pkgver.tar.gz pcre.patch)
md5sums=('e3b1f5ebd24aac03aacb38ec183eb426' 'a11774428cb7e97a81107a22682d1798')
url="http://freeworld.thc.org/releases.php"
license='custom'
arch=('i686')

build() {
  cd $startdir/src/$pkgname-$pkgver

  mkdir -p $startdir/pkg/usr/{bin,man/man1,share/amap,share/licenses/amap}
  
  sed -i -e "s:etc/:share/amap/:g" amap-lib.c
  sed -i 's:/usr/local:/usr:' amap.h
  sed -i '/DATADIR/s:/etc:/share/amap:' Makefile.am

  rm -rf pcre-3.9

  patch -Np1 -i ../pcre.patch || return 1

  ./configure --prefix=/usr

  sed -i -e '/^XLIBPATHS/s:=.*:=:' -e '/^XIPATHS=/s:=.*:=:' Makefile

  make PREFIX=$startdir/pkg/usr install  
  cp LICENCE.AMAP $startdir/pkg/usr/share/licenses/amap
}
