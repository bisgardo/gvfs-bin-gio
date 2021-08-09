# gvfs-bin-gio

This project consists of a small collection of compatibility scripts for the obsolete
binaries (`gvfs-*`) that used to be a part of the
[`gvfs`](https://wiki.gnome.org/Projects/gvfs) project.
The files are structured as expected by `dpkg-deb` for turning them into a Debian package.

The scripts, which are verbatim copies from the Ubuntu package
[`gvfs-bin`](https://packages.ubuntu.com/focal/gvfs-bin),
delegate all calls directly to the [`gio`](https://docs.gtk.org/gio/) tool.

Ever since the binaries were deprecated and their implementations
[replaced](https://gitlab.gnome.org/GNOME/gvfs/-/commit/2f28fa49cfeb1c82927a1c7c0021b15e2742149f)
by the `gio` wrapper scripts in 2016,
the `gvfs-bin` package has shipped just those scripts.

In 2018, the scripts were
[removed](https://gitlab.gnome.org/GNOME/gvfs/-/commit/6d711c07cbd00768c6b2b468f3100f02afc58f6f)
from the `gvfs` code repository entirely.
And as of Ubuntu 20.10, the package is no longer present in the official repositories.

This project was created to retain compatibility with these tools in newer versions of Ubuntu,
where they may be needed for legacy reasons.

As the only dependency of the package is no particular version of `libglib2.0-bin`
(for installing `gio`),
it's also expected to work on Debian-based systems other than Ubuntu.

## Build Debian package

```shell
dpkg-deb --build gvfs-bin-gio
```

## Install Debian package

```shell
sudo apt install ./gvfs-bin-gio.deb
```

## License

[LGPL-2.1](./LICENSE) (following the source package's
[copyright](https://changelogs.ubuntu.com/changelogs/pool/main/g/gvfs/gvfs_1.44.1-1ubuntu1/copyright)
file).
