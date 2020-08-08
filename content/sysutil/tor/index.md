---
title: Tor
image: logos/tor.png
---

Tor (short for [**T**he **O**nion **R**outer](https://www.torproject.org/)) is software that provides an increased level of privacy by anonymizing your internet traffic.
It does so by using multiple layers of encryption and routing traffic through multiple nodes of the Tor network.

This guide will show how to install Tor on FreeBSD.

## Installing

In order to ensure we get the latest version of Tor, let's build and install from the [ports tree](/portstree/):

```shell
cd /usr/ports/security/tor
sudo make install clean
```

## Conclusion

With `tor` successfully installed, we can make sure the `rcvar` is set with:

```shell
sudo sysrc tor_enable="YES"
```

...and then start it with:

```shell
sudo service tor start
```

Tor's configuration file is located at `/usr/local/etc/tor/torrc`.
This is where you can set various configurations and functionalities for Tor, such as establishing Tor Hidden Services.

For further reading:
* [Overview of the Tor Project.](https://2019.www.torproject.org/about/overview.html.en)
* [History of Tor](https://www.torproject.org/about/history/).
* [Tor Relay Guide](https://trac.torproject.org/projects/tor/wiki/TorRelayGuide)
