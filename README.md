## uAu (unattended Arch upgrade) package build

package build for uau (https://github.com/steadfasterX/arch_uau/)

## Guide

### Install the requirements

`gpg --receive-keys 1D1F0DC78F173680`

`yaourt -S --noconfirm aur-comment-fetcher-git checkupdates+aur python3-memoizedb`

#### optional: Install mail

If you have the command `mail` **not** available on your system:

`sudo pacman -S sstmp`

I use and have tested only sstmp but every sendmail-like `mail` cmd will do.

#### Build & Install

`makepkg -si`

#### Configure

*TBD*

