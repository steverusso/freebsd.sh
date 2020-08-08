---
title: Caddy
image: logos/caddy.png
---

Caddy is a web server that is [open source](https://github.com/mholt/caddy/), [feature rich](https://caddyserver.com/features), and very easy to use.
This guide will show how to install Caddy on FreeBSD.

## Installing Caddy

Caddy can be installed via `pkg`:

```shell
sudo pkg install caddy
```

or built from source using the [ports tree](/portstree/):

```shell
cd /usr/ports/www/caddy
sudo make install clean
```

(**Note:** Caddy can also be built from source [using Git and Go](https://github.com/mholt/caddy/#build), but we will not be covering that process in this guide.)

## Running Caddy As Service

#### 1. Setting the Necessary `rc` Variables

After installation via `ports` or `pkg`, there are a few more things to do before we can run Caddy as a service.
First, we have to set the `caddy_enable` and `caddy_cert_email` rc variables.

The `caddy_enable` variable must be set to `YES` so that we can start Caddy as a service.
The `caddy_cert_email` variable, from the [Caddy docs](https://caddyserver.com/docs), is "the email address used to generate a certificate with a trusted CA."
By setting this variable here, we won't be prompted for it when we run Caddy, allowing it to run automatically.

We could set these values manually, by editing `/etc/rc.conf` directly.
However, the safer way is to use the `sysrc` command as follows:

```shell
sudo sysrc caddy_enable="YES"
sudo sysrc caddy_cert_email="<your_email_address>"
```

#### 2. Creating a `Caddyfile`

Next, we need to have a readable file named `Caddyfile` in Caddy's root directory, which by default is `/usr/local/www`.
The Caddyfile does not need any content yet. It just needs to exist.
If we try to start Caddy without it, we will get an error message: `/usr/local/etc/rc.d/caddy: WARNING: /usr/local/www/Caddyfile is not readable`.

Therefore, we just need to create the `/usr/local/www` directory and put a file named `Caddyfile` there:

```shell
sudo mkdir /usr/local/www
sudo touch /usr/local/www/Caddyfile
```

#### 3. Starting Caddy Service

Now we are all set to go ahead and start Caddy!

```shell
sudo service caddy start
```

## Conlusion

To get started with using Caddy, check the [user guide](https://caddyserver.com/docs) and [GitHub repo](https://github.com/mholt/caddy).
