## uAu (unattended Arch upgrade) package build

package build for uau (https://github.com/steadfasterX/arch_uau/)

## Guide

### Install the requirements

`gpg --receive-keys 1D1F0DC78F173680`

`yay -S --noconfirm aur-comment-fetcher-git checkupdates+aur python3-memoizedb`

#### optional: Install mail

If you have the command `mail` **not** available on your system:

`yay -S ssmtp s-nail`

I use and have tested only sstmp but every sendmail-like `mail` cmd will do.

#### Build & Install

`git clone https://github.com/steadfasterX/arch_uau-pkg.git`

`cd arch_uau-pkg` 

`makepkg -si`

#### Configure

*/etc/unattended-arch-upgrade.conf*

All options are well documented in that conf file. Just adjust it to your needs.

*/etc/unattended-arch-upgrade.ignore*

This one should be used VERY carefully as ignoring packages can result in unexpected system behavior.
Each "IgnorePkg=" can just contain 1 package name.

Bad example: libraries
Good example: kernel

