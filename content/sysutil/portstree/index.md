---
title: Ports Tree
---

FreeBSD's port system provides an organized way to build and install software from source.
One advantage of using the ports tree is that the ports are usually more up-to-date than the precompiled binaries available via `pkg`.

## Fetch / Update the Ports Tree

The FreeBSD base system has a utility called `portsnap` that is used to manage the ports tree.
Let's use it to first download the ports tree:

```shell
sudo portsnap fetch extract
```

This will download and install the ports hierarchy to `/usr/ports`.

If you already have the ports tree, we can make sure it's up to date by running:

```shell
sudo portsnap update
```

## Installing a Port

A port can now be installed by navigating to it's directory in the ports tree and running the `make` build commands.
For example:

```shell
cd /usr/ports/ports-mgmt/portmaster
make install clean
```

## Removing a Port

Removing a port is easy too.
Simply navigate to it's directory in the ports tree and run the `make deinstall`.
For example:

```shell
cd /usr/ports/ports-mgmt/portmaster
make deinstall
```
