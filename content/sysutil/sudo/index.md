---
title: Sudo
image: logos/sudo.png
---

[Sudo](https://www.sudo.ws/) is a program that allows a user with elevated privileges to delegate authority to other users (or groups of users) so that they can run commands as root.
Instead of running `su root` everytime you need to run a command as root, you can just preface the command with `sudo`.
This guide will show how to install and configure `sudo` on FreeBSD.

(**Note:** All commands in this guide must be run as root. Run `su root` to log in as the root user.)

## Installing Sudo

Sudo can be installed via `pkg`:

```shell
pkg install sudo
```

or built from source using the [ports tree](/portstree/):

```shell
cd /usr/ports/security/sudo
make install clean
```

## Configuring Sudo

After installation, we have to authorize any non-root user (or group) so they can use sudo effectively.
Edit the `/usr/local/etc/sudoers` file as root.
Look for the following line:

```
root ALL=(ALL) ALL
```

We can simply copy and paste that line, and then change the word `root` to a user account we would like to authorize, like this:

```
<user_name> ALL=(ALL) ALL
```

We can even set it so that the authorized user doesn't have to enter a password to run root commands with sudo:

```
<user_name> ALL=(ALL) NOPASSWD: ALL
```

## Conclusion

Now that sudo is installed, log in as one of the authorized users in the `sudoers` file and try running a command that needs root access.
For example:

```shell
sudo pkg update
```

If a command like that works, then that means sudo is installed and configured correctly!
