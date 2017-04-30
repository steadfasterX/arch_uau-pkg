pkgname=uau
pkgver=0.0.1
pkgrel=1
pkgdesc="uAu - unattended Arch upgrade is a little helper to damage your system by installing Arch upgrades non-interactively"
arch=('any')
url="https://github.com/steadfasterX/arch_uau"
license=('LGPL-3.0')
depends=('aur-comment-fetcher-git' 'checkupdates+aur' 'sudo' 'pacman' 'python3-memoizedb')
makedepends=('git')
optdepends=('ssmtp')
backup=('etc/unattended-arch-upgrade.conf' 'etc/unattended-arch-upgrade.ignore')
source=("https://github.com/steadfasterX/arch_$pkgname/archive/v$pkgver.tar.gz")
md5sums=('SKIP')
BINFIX=usr/local/bin
SUDOERS=etc/sudoers.d
SYSD=etc/systemd/system
MANDIR=usr/share/man
MAN5DIR=${MANDIR}/man5
MAN8DIR=${MANDIR}/man8
MAN5PAGE=uau.5
MAN8PAGE=uau.8
USER=root
GROUP=root
UPDATEUSER=archupdater
install=${pkgname}.install

#build() {
#    
#}

package() {
    cd "arch_$pkgname-$pkgver"

    #install -o ${USER} -g ${GROUP} -m 0755 bin/uau-archnews ${BINFIX}/uau-archnews
    mkdir -p $pkgdir/etc/cron.d $pkgdir/${SUDOERS} $pkgdir/${BINFIX} $pkgdir/$SYSD $pkgdir/$MAN5DIR $pkgdir/$MAN8DIR
    install -o ${USER} -g ${GROUP} -m 0755 $BINFIX/* $pkgdir/${BINFIX}
    ln -sfv $pkgdir/${BINFIX}/uau $pkgdir/${BINFIX}/unattended-upgrade
    install -o ${USER} -g ${GROUP} -m 0700 conf/uau_sudo $pkgdir/${SUDOERS}/uau_sudo
    install -o ${USER} -g ${GROUP} -m 0744 conf/unattended-arch-upgrade.conf $pkgdir/etc/unattended-arch-upgrade.conf
    install -o ${USER} -g ${GROUP} -m 0744 conf/unattended-arch-upgrade.ignore $pkgdir/etc/unattended-arch-upgrade.ignore
    install -o ${USER} -g ${GROUP} -m 0755 conf/archnews_cron $pkgdir/etc/cron.d/archnews
    install -o ${USER} -g ${GROUP} -m 0755 conf/unattended-arch-upgrade.service $pkgdir/${SYSD}/unattended-arch-upgrade.service
    install -o ${USER} -g ${GROUP} -m 0755 conf/unattended-arch-upgrade.timer $pkgdir/${SYSD}/unattended-arch-upgrade.timer

    install -m 0644 doc/${MAN5PAGE} $pkgdir/${MAN5DIR}/${MAN5PAGE}
    install -m 0644 doc/${MAN8PAGE} $pkgdir/${MAN8DIR}/${MAN8PAGE}

    mkdir -p "$pkgdir/usr/share/licenses/$pkgname"
    install -D -m644 ./LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

}

