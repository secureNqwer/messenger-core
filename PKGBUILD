# Maintainer: secureNqwer
# Build from source (supports auto-update via git pull)
pkgname=zerolink
pkgver=1.0.0
pkgrel=1
pkgdesc="Secure P2P Messenger with ZeroTier"
arch=("x86_64" "aarch64")
url="https://github.com/secureNqwer/messenger-core"
license=("MIT")
depends=("glibc" "gcc-libs")
makedepends=("go" "git" "cmake" "make" "base-devel")
provides=("zerolink")
conflicts=("zerolink-bin")

build() {
  cd "$srcdir/$pkgname"
  bash scripts/build_libzt.sh
  make client
  make server
}

package() {
  cd "$srcdir/$pkgname"
  install -Dm755 bin/zerolink "$pkgdir/usr/bin/zerolink"
  install -Dm755 bin/zerolink-server "$pkgdir/usr/bin/zerolink-server"
  install -Dm644 zerolink.desktop.in "$pkgdir/usr/share/applications/zerolink.desktop"
  # Fix Exec path
  sed -i "s|EXEC|/usr/bin/zerolink|" "$pkgdir/usr/share/applications/zerolink.desktop"
}
