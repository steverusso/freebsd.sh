---
title: Go
image: logos/golang.png
---

Go (aka. [Golang](https://golang.org/)) is a programming language developed by a team at Google.
It is open source and distrubted under a BSD-style license.
This guide will show how to install Go on FreeBSD.

## Installing

Go can be installed via `pkg`:

```shell
sudo pkg install go
```

or built from source using the [ports tree](/portstree/):

```shell
cd /usr/ports/lang/go
sudo make install clean
```

## Configuring

Go uses environment variables for configuration.
If Go was installed via `ports` or `pkg`, then the defaults are all set.
We can see what those are by running:

```shell
go env
```

However, the actual environment variables themselves might not be set.
For example, we can see if a value is set by running:

```shell
echo $GOPATH
```

That will likely be empty, which is fine since Go already knows where to look / what directory to use.
However, if we want to reference `$GOPATH` in shell commands (without typing `` `go env GOPATH` `` every time), we need to explicity set it.
We can do so by adding the following line to our `~/.profile` file:

```shell
export GOPATH=`go env GOPATH` # Location of Go workspace.
```

Finally, we can add the `bin` directory from our Go workspace to our `$PATH` environment variable:

```shell
export PATH=$PATH:$GOPATH/bin # Add workspace bin directory to PATH variable.
```

## Checking Install

To make sure we installed Go correctly, we can try running a small test program.
First, create a file called `main.go` with the following content:

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, World!")
}
```

Then, do:

```shell
go run main.go
```

If that outputs `Hello, World!`, then that means everything is installed correctly!

## Conclusion

If you're new to Go, you can take a [tour of Go](https://tour.golang.org/welcome/1) to get more familiar!

For a list of really cool Go projects, check out [awesome-go](https://github.com/avelino/awesome-go).
