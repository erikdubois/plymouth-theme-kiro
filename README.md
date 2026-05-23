<p align="center">
  <img src="kiro.jpg" alt="Kiro" width="220" />
</p>

# plymouth-theme-kiro

A Plymouth boot splash theme for Arch / Kiro Linux based on the Alienware look — a polished, full-screen splash for the Kiro distro's boot sequence. Part of the `~/EDU/` learning series.

## What's in this repo

- `usr/share/plymouth/themes/` — the Plymouth theme assets (`*.plymouth` manifest, `*.script` animation, image frames).
- `setup.sh`, `up.sh` — standard EDU bash scaffold.

## Companion repo

- [plymouth-theme-startrek](https://github.com/erikdubois/plymouth-theme-startrek) — Star Trek Starfleet flavoured sibling theme.

## Installation

### From `nemesis_repo` (recommended)

```ini
[nemesis_repo]
SigLevel = Never
Server = https://erikdubois.github.io/$repo/$arch
```

```bash
sudo pacman -Syu
sudo pacman -S plymouth-theme-kiro
```

You'll also need Plymouth:

```bash
sudo pacman -S plymouth
```

### Manual

```bash
git clone https://github.com/erikdubois/plymouth-theme-kiro.git
cd plymouth-theme-kiro
sudo cp -r usr/share/plymouth/themes/. /usr/share/plymouth/themes/
```

### Activate

Add `plymouth` to `HOOKS` in `/etc/mkinitcpio.conf` (immediately after `base udev`), then set the theme and rebuild initramfs:

```bash
sudo plymouth-set-default-theme -R kiro
```

Make sure `quiet splash` is in `GRUB_CMDLINE_LINUX_DEFAULT` in `/etc/default/grub`, then regenerate the GRUB config:

```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Reboot.

## Test without rebooting

```bash
sudo plymouthd --debug --tty=tty1
sudo plymouth --show-splash
# leave it visible for a few seconds, then:
sudo plymouth --quit
```

Run from a TTY (Ctrl+Alt+F2), not from inside your graphical session.

## Websites

Information : https://erikdubois.be

## Social Media

Youtube : https://www.youtube.com/erikdubois

## License

See [LICENSE](./LICENSE).
