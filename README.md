ldc2.snap
=========

This project defines a snap package for LDC, the LLVM-based compiler for
the D programming language.  It is an 'external' snap, meaning that it
downloads and builds the source from the official LDC git repo.

The LDC project aims to provide a portable compiler for the D language,
with modern optimization and code generation capabilities.  It uses the
official DMD compiler frontend to support the latest version of D2, and
uses the LLVM Core libraries for code generation.  For more information
on LDC, see: https://github.com/ldc-developers/ldc

The D programming language is a systems programming language with C-like
syntax and static typing.  It combines efficiency, control and modelling
power with safety and programmer productivity.  For more information on
the D language, see: https://dlang.org/

Snap packages are designed to provide secure, containerized applications
that are appropriately sandboxed away from the rest of the system they
are running on.  For more information on snap packages, see:
http://snapcraft.io/


Building
--------

On Ubuntu 16.04 with snapcraft installed (`sudo apt install snapcraft`):

    git clone https://github.com/WebDrake/ldc2.snap.git
    cd ldc2.snap
    snapcraft

To ensure a clean build, install lxd (`sudo apt install lxd`), configure
its network settings, and then:

    snapcraft cleanbuild


Installing
----------

Self-built snaps are unsigned, so installing them requires the use of
the `--dangerous` flag:

    sudo snap install --dangerous ldc2_1.0.0_amd64.snap


Known issues
------------

The containerized LDC compiler will be unable to link code against host
system libraries, since it has no way to access them.  This in effect
means that it is currently limited to compiling code whose dependencies
are limited to druntime and phobos.

This issues is expected to be resolved with future releases of `snapd`
and `snapcraft` but means that, for now, this package is presented as a
tech preview only, and is not recommended for production use.
