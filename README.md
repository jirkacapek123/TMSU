![TMSU](http://tmsu.org/images/tmsu.png)

<!--[![Build Status](https://travis-ci.org/oniony/TMSU.svg?branch=master)](https://travis-ci.org/oniony/TMSU)
[![Go Report Card](https://goreportcard.com/badge/github.com/oniony/TMSU)](https://goreportcard.com/report/github.com/oniony/TMSU)-->

Overview
========

TMSU is a tool for tagging your files. It provides a simple command-line utility
for applying tags and a virtual filesystem to give you a tag-based view of your
files from any other program.

TMSU does not alter your files in any way: they remain unchanged on disk, or on
the network, wherever your put them. TMSU maintains its own database and you
simply gain an additional view, which you can mount where you like, based upon
the tags you set up.

Usage
=====

Before you can get tagging, you'll need to initialise a TMSU database:

    $ cd ~
    $ tmsu init

This database will be used automatically whenever you are under that
directory. In this case we created one under the home directory.

You can tag a file by specifying the file and the list of tags to apply:

    $ tmsu tag banana.jpg fruit art year=2015

Or you can apply tags to multiple files:

    $ tmsu tag --tags="fruit still-life art" banana.jpg apple.png

You can query for files with or without particular tags:

    $ tmsu files fruit and not still-life

Mount the virtual filesystem to an empty directory:

    $ mkdir mp
    $ tmsu mount mp
    
A subcommand overview and detail on how to use each subcommand is available via the
integrated help:

    $ tmsu help
    $ tmsu help tags

Documentation is maintained online on the wiki:

  * <https://github.com/oniony/TMSU/wiki>

Installing
==========

<!--Packages
--------

Thanks to the efforts of contributors using these platforms, packages are available
for the following GNU/Linux distributions:

  * Ubuntu
    - Stable <https://launchpad.net/~tmsu/+archive/ubuntu/ppa>
    - Daily <https://launchpad.net/~tmsu/+archive/ubuntu/daily>
  * Arch
    - Stable <https://aur.archlinux.org/packages/tmsu/>
  * Nix/NixOS
    - Stable <https://search.nixos.org/packages?query=tmsu&show=tmsu>
    - Unstable <https://search.nixos.org/packages?query=tmsu&show=tmsu&channel=unstable>

These packages are not maintained by me and I cannot guarantee their content.-->

Binary
------

Binary builds for a limited number of architectures and operating system
combinations are available:

  * <https://github.com/oniony/TMSU/releases>

You will need to ensure that both FUSE and Sqlite3 are installed for the
program to function. These packages are typically available with your
operating system's package management system. (If you install TMSU using one
of the above packages, these should be installed automatically.)

1. Install the binary

    Copy the program binary. The location may be different for your operating
    system:

on Linux:
        $ cp bin/tmsu ~/.local/bin

<!--2. Optional: Zsh completion

    Copy the Zsh completion file to the Zsh site-functions directory:

        $ cp misc/zsh/_tmsu /usr/share/zsh/site-functions-->

From Source
-----------

If you would rather build from the source code then please see `COMPILING.md`
in the root of the repository.

About
=====

TMSU is written in Go: <http://www.golang.org/>

Much of the functionality the program provides is made possible by the FUSE and
Sqlite3 libraries, their Go bindings and the Go language standard library.

  * Website: <http://tmsu.org/>
  * Project: <https://github.com/oniony/TMSU/>
  * Wiki: <https://github.com/oniony/TMSU/wiki>
  * Issue tracker: <https://github.com/oniony/TMSU/issues>

Release Notes
=============


- - -

Copyright 2011-2018 Paul Ruane

Copying and distribution of this file, with or without modification,
are permitted in any medium without royalty provided the copyright
notice and this notice are preserved.  This file is offered as-is,
without any warranty.
