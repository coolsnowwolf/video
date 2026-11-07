# Video packages feed

## Description

This is an OpenWrt package feed containing video / graphics (as in 'higher than just curses') related libraries and applications which are not considered to be so called "core" packages.

## Usage

To use these packages, add the following line to the feeds.conf
in the OpenWrt buildroot:

```
src-git video https://github.com/coolsnowwolf/video
```

This feed should be included and enabled by default in the OpenWrt buildroot. To install all its package definitions, run:

```
./scripts/feeds update video
./scripts/feeds install -a -p video
```

The video packages should now appear in menuconfig in section 'Video'.

This feed includes libdrm 2.4.133 with separate GPU driver packages and
accel-support for render and compute device permissions, imported from QWRT.
If libdrm is already installed from another feed, switch its package definition
before installing Mesa:

```
./scripts/feeds uninstall libdrm
./scripts/feeds install -p video libdrm accel-support
```

On a buildroot that provides libdrm as a core package, use
`./scripts/feeds install -f -p video libdrm accel-support` to override it.
