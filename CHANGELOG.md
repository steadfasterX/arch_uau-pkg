## Changelog

### v3.0.0

Major rewrite of several parts to remove outdated dependencies.

**Manual action required**

If you upgrade from a previous release please check the new settings especially check the new paths and names!

Example:

```
sdiff -s /etc/unattended-arch-upgrade.conf /etc/unattended-arch-upgrade.conf.pacnew
```

Requirements:

- added: `python-feedparser`
- added (opt): msmtp (alternative to ssmtp which moved to AUR)
- removed: `archnews2`
- removed: `python3-memoizedb`

Changes:

- all executables have been moved to `/usr/bin` (before `/usr/local/bin`)
- added: `uau-news-parser` - a complete re-write of the buggy previous approach
    - incl. enhanced output and several fixes
    - new option: `--html` (--text is set as default)
- added: `uau-package-parser` - a complete re-write of the buggy previous approach
    - incl. enhanced output/parsing
    - new option: `--html` (--text set as default)
- renamed: `uau-archnews` -> `uau-news-wrapper`
- removed: read/unread options for Arch news feed
- added: `90-uau-reboot-required.hook` which creates an indicator file to detect common reasons for a reboot
- added: warning within the update mail when a reboot is suggested
- added: package lists (with and without AUR)
- added: this changelog ;)

Fixes:

- fix: using `yay` instead of `trizen` for AUR operations
- fix: migrating `egrep` -> `grep -E`, thanks to @asm0dey
- fix: be more POSIX compliant, thanks to @rgcv
- fix: better mail subject for info vs. real update
- fix: use mail var instead of hard-coded `mail`
- fix: news feed args were not shown always

