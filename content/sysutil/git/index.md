---
title: Git
image: logos/git.png
---

Git is one of the most widely used distributed version control systems.
This guide will show how to install and configure Git on FreeBSD.

## Installing

Git can be installed via `pkg`:

```shell
sudo pkg install git
```

or built from source using the [ports tree](/portstree/):

```shell
cd /usr/ports/devel/git
sudo make install clean
```

## Configuring

Let's make some basic (yet very useful) git configurations.
First, let's set a user name and email:

```shell
git config --global user.name "<your_user_name>"
git config --global user.email "<your_email_address>"
```

Next, let's set our default editor:

```shell
git config --global core.editor "vim"
```

Finally, we can check that our configurations are set correctly by running:

```shell
git config --list
```

(**Note:** these configurations are stored in the `~/.gitconfig` file.)

## Conclusion

For further reading, check out the [online Git Book](https://git-scm.com/book/en/v2) written by Scott Chacon and Ben Straub.
It's a great resource for learning how to use Git.
