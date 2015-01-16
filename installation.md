---
title: Installation
layout: slate
---

### Installation

To install a stable release:

    tar -xzf cpuaff-x.x.x.tar.gz
    cd cpuaff-x.x.x
    ./configure
    make
    make install

To install from a repository snapshot:

    tar -xzf <tarball>
    cd <tarball directory>
    aclocal
    autoconf
    autoheader
    automake -c --add-missing
    ./configure
    make
    make install

