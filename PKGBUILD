# Maintainer: Philipp Nowak <packages@lit.plus>
pkgname=kafkaesque-bin
pkgver=2.5.1
pkgrel=1
pkgdesc="Kafka development tool"
arch=('x86_64')
url="https://github.com/literalplus/kafkaesque-pkgbuild"
license=('GPL')
# Depends:
# libblkid1, libmount1, libuuid1 -> util-linux-libs
# libc6, -> glibc
# libdbus-1-3 -> dbus
# libexpat1 -> expat
# libgpg-error0 -> libgpg-error
# liblzma5 -> xz
# libpcre3 -> pcre
# libselinux1 -> ?
# libsystemd0
# xdg-utils =
#zlib1g = zlib

# unclear if it really needs all those....
# namcap flags as not needed: xdg-utils

depends=('util-linux-libs' 'glibc' 'dbus' 'expat' 'libgpg-error' 'xz' 'pcre' 'systemd-libs' 'zlib')
makedepends=()
source=("${pkgname}-${pkgver}.deb::https://github.com/patschuh/KafkaEsque/releases/download/v${pkgver}/kafkaesque_${pkgver}-${pkgrel}_amd64.deb")
sha256sums=('f116c847b312164a6931a4bdfac0bcdb232d0be5471547043b4d39ea59842acd')

prepare() {
    cd "$srcdir"
    /usr/bin/ar p "${pkgname}-${pkgver}.deb" data.tar.zst | bsdtar xf -
}

package() {
    cd "$srcdir"
    cp -R opt "${pkgdir}/opt"
    chmod 755 "${pkgdir}/opt/kafkaesque/bin/KafkaEsque"
    mkdir -p "${pkgdir}/usr/bin"
    mkdir -p "${pkgdir}/usr/share/applications"
    ln -sf "/opt/kafkaesque/bin/KafkaEsque" "${pkgdir}/usr/bin/KafkaEsque"
    ln -sf "/opt/kafkaesque/lib/kafkaesque-KafkaEsque.desktop" "${pkgdir}/usr/share/applications/KafkaEsque.desktop"
}
