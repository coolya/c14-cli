# C14 CLI

Interact with Online C14 API from the command line.

![Online C14 logo](https://raw.githubusercontent.com/QuentinPerez/c14-cli/master/assets/logo.png)

#### Table of Contents

1. [Overview](#overview)
2. [Setup](#setup)
3. [Usage](#usage)
  * [Login](#login)
  * [Commands](#commands)
    * [`create`](#c14-create)
    * [`freeze`](#c14-freeze)
    * [`help`](#c14-help)
    * [`list`](#c14-list)
    * [`login`](#c14-login)
    * [`ls-files`](#c14-ls-files)
    * [`rename`](#c14-rename)
    * [`remove`](#c14-remove)
    * [`unfreeze`](#c14-unfreeze)
    * [`upload`](#c14-upload)
  * [Examples](#examples)
4. [Changelog](#changelog)
5. [Development](#development)
  * [Hack](#hack)
6. [License](#license)

## Overview

A command-line tool to manage your C14 storage easily

## Setup

```shell
go install github.com/QuentinPerez/c14-cli/cmd/c14
```

## Usage


```console
$ Usage: c14 [OPTIONS] COMMAND [arg...]

Interact with C14 from the command line.

Options:
  -D, --debug        Enable debug mode
  -V, --verbose      Enable verbose mode

Commands:
    create    Create a new archive
    freeze    Lock an archive
    help      Help of the c14 command line
    list      List archives
    login     Log in to Online API
    ls-files  List the archive files
    rename    Rename an archive
    remove    Remove an archive
    unfreeze  Unlock an archive
    upload    Upload your file or directory into an archive

Run 'c14 COMMAND --help' for more information on a command.
```

### Login

```console
$ c14 login
Please opens this link with your browser: https://console.online.net/oauth/v2/device/usercode
Then copy paste the code XXXXXX
$
```

### Commands

#### `c14 create`

```console
Usage: c14 create [OPTIONS]

Create a new archive, By default with a random name

Options:
  -d, --description=""  Assigns a description
  -h, --help=false      Print usage
  -n, --name=""         Assigns a name
  -q, --quiet=false     Don't display the waiting loop

Examples:
		$ c14 create
		$ c14 create --name "MyAchive"
```


#### `c14 freeze`

```console
Usage: c14 freeze [OPTIONS] [ARCHIVE]+

Lock an archive

Options:
  -h, --help=false      Print usage
  --nowait=false
  -q, --quiet=false

Examples:
        $ c14 freeze 83b93179-32e0-11e6-be10-10604b9b0ad9
```


#### `c14 help`

```console
Usage: c14 help [COMMAND]

Help prints help information about c14 and its commands.
By default, help lists available commands.
When invoked with a command name, it prints the usage and the help of
the command.

Options:
  -h, --help=false      Print usage

Examples:
    $ c14 help
    $ c14 help create
```


#### `c14 login`

```console
Usage: c14 login

Generates a credentials file in $HOME/.c14rc
containing informations to generate a token

Options:
  -h, --help=false      Print usage

Examples:
    $ c14 login
```


#### `c14 list`

```console
Usage: c14 ls-files ARCHIVE

List the archive files.

Options:
  -h, --help=false      Print usage

Examples:
        $ c14 ls-files 83b93179-32e0-11e6-be10-10604b9b0ad9
```


#### `c14 rename`

```console
Usage: c14 rename ARCHIVE new_name

Rename an archive

Options:
  -h, --help=false      Print usage

Examples:
        $ c14 rename 83b93179-32e0-11e6-be10-10604b9b0ad9 courses
        $ c14 rename courses coursesJan
```


#### `c14 remove`

```console
Usage: c14 remove [ARCHIVE]+

Remove an archive

Options:
  -h, --help=false      Print usage

Examples:
        $ c14 remove 83b93179-32e0-11e6-be10-10604b9b0ad9 2d752399-429f-447f-85cd-c6104dfed5db
```


#### `c14 unfreeze`

```console
Usage: c14 unfreeze [OPTIONS] [ARCHIVE]+

Unlock an archive

Options:
  -h, --help=false      Print usage
  --nowait=false
  -q, --quiet=false

Examples:
        $ c14 unfreeze 83b93179-32e0-11e6-be10-10604b9b0ad9
```


#### `c14 upload`

```console
Usage: c14 upload [DIR|FILE]* ARCHIVE

Upload your file or directory into an archive.

Options:
  -h, --help=false      Print usage
  -n, --name=""         Assigns a name (only with tar method)
  --tar=false           Read a tar form stdin

Examples:
        $ c14 upload
        $ c14 upload test.go 83b93179-32e0-11e6-be10-10604b9b0ad9
        $ c14 upload /upload 83b93179-32e0-11e6-be10-10604b9b0ad9
        $ tar cvf - /upload 2> /dev/null | ./c14 upload --tar --name "file.tar.gz" fervent_austin
```



### Examples

Soon

---

## Changelog

### master (unreleased)

 * Support of `create` command
 * Support of `freeze` command
 * Support of `help` command
 * Support of `list` command
 * Support of `login` command
 * Support of `ls-files` command
 * Support of `rename` command
 * Support of `remove` command
 * Support of `unfreeze` command
 * Support of `upload` command

---

## Development

Feel free to contribute :smiley::beers:


### Hack

1. [Install go](https://golang.org/doc/install)
2. Ensure you have `$GOPATH` and `$PATH` well configured, something like:
  * `export GOPATH=$HOME/go`
  * `export PATH=$PATH:$GOPATH/bin`
3. Fetch the project: `go get -u github.com/QuentinPerez/c14-cli`
4. Go to c14-cli directory: `cd $GOPATH/src/github.com/QuentinPerez/c14-cli`
5. Hack: `vim`
6. Build: `make`
7. Run: `./c14`

## License

[MIT](https://github.com/QuentinPerez/c14-cli/blob/master/LICENSE.md)