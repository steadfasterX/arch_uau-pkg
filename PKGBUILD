# Maintainer: steadfasterX <steadfasterX [at] binbash -dot- rocks>
pkgname=uau
pkgver=3.0.0
pkgrel=2
pkgdesc="unattended upgrades for Arch. Schedule automatic upgrades while respecting the recommended upgrade process (Arch wiki - System maintenance)."
arch=('any')
url="https://github.com/steadfasterX/arch_uau"
license=('LGPL3')
depends=('python-feedparser' 'sudo')
makedepends=('git')
optdepends=('ssmtp: extreme simple Mail Transport Agent|msmtp: mini smtp client' 's-nail: to provide the mail(x) command' 'yay' 'aur-comment-fetcher-git')
backup=('etc/unattended-arch-upgrade.conf' 'etc/unattended-arch-upgrade.ignore')
source=("https://github.com/steadfasterX/arch_$pkgname/archive/v$pkgver.tar.gz")
changelog="CHANGELOG.md"
sha256sums=('9b5d87a6ac22ef558c0adaebcb815b79d3416e874750cb6f934dab6bcbc9149b')
BINFIX=usr/bin
SUDOERS=etc/sudoers.d
SYSD=etc/systemd/system
MANDIR=usr/share/man
MAN5DIR=${MANDIR}/man5
MAN8DIR=${MANDIR}/man8
MAN5PAGE=uau.5
MAN8PAGE=uau.8
USER=root
GROUP=root
install=${pkgname}.install

package() {
    cd "arch_$pkgname-$pkgver"

    mkdir -p $pkgdir/etc/cron.d $pkgdir/${BINFIX} $pkgdir/$SYSD $pkgdir/$MAN5DIR $pkgdir/$MAN8DIR $pkgdir/etc/pacman.d/hooks

    install -d -m 0750 $pkgdir/${SUDOERS}
    install -o ${USER} -g ${GROUP} -m 0700 conf/uau_sudo $pkgdir/${SUDOERS}/uau_sudo
    install -o ${USER} -g ${GROUP} -m 0644 conf/unattended-arch-upgrade.conf $pkgdir/etc/unattended-arch-upgrade.conf
    install -o ${USER} -g ${GROUP} -m 0644 conf/unattended-arch-upgrade.ignore $pkgdir/etc/unattended-arch-upgrade.ignore
    install -o ${USER} -g ${GROUP} -m 0755 bin/* $pkgdir/${BINFIX}/
    ln -sfv uau $pkgdir/${BINFIX}/unattended-upgrade
    install -o ${USER} -g ${GROUP} -m 0644 conf/archnews_cron $pkgdir/etc/cron.d/archnews
    install -o ${USER} -g ${GROUP} -m 0755 conf/unattended-arch-upgrade.service $pkgdir/${SYSD}/unattended-arch-upgrade.service
    install -o ${USER} -g ${GROUP} -m 0755 conf/unattended-arch-upgrade.timer $pkgdir/${SYSD}/unattended-arch-upgrade.timer
    install -o ${USER} -g ${GROUP} -m 0644 conf/uau.hook $pkgdir/etc/pacman.d/hooks/90-uau-reboot-required.hook

    install -m 0644 doc/${MAN5PAGE} $pkgdir/${MAN5DIR}/${MAN5PAGE}
    install -m 0644 doc/${MAN8PAGE} $pkgdir/${MAN8DIR}/${MAN8PAGE}

    mkdir -p "$pkgdir/usr/share/licenses/$pkgname"
    install -D -m644 ./LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

