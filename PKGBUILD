# Maintainer : Ebubekir KARUL <ebubekirkarul@yandex.com>
# Contributor: Tom K <tomk@runbox.com>
# Contributor: kastor <kastor@fobos.org.ar>
# Contributor : sebikul <sebikul@gmail.com>

pkgname=amap
pkgver=5.4
pkgrel=1
pkgdesc="Next-generation tool for assisting network penetration testing."
arch=('any')
license=('GPL2 ''custom')
depends=('glibc' 'pcre' 'openssl')
url="http://freeworld.thc.org/releases.php"
source=(http://freeworld.thc.org/releases/$pkgname-$pkgver.tar.gz)
md5sums=('2617c13b0738455c0e61c6e980b8decc')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}

  ./configure

  make
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}
  
  install -Dm755 amap $pkgdir/usr/bin/amap
  ln $pkgdir/usr/bin/amap $pkgdir/usr/bin/amap6
  install -Dm755 amapcrap $pkgdir/usr/bin/amapcrap
  
  mkdir -p $pkgdir/etc
  install -Dm644 appdefs.* $pkgdir/etc
  
  install -Dm644 amap.1 $pkgdir/usr/share/man/man1/amap.1
  
  install -Dm644 LICENCE.AMAP $pkgdir/usr/share/licenses/$pkgname/LICENCE
  
}