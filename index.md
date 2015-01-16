---
title: Home
layout: slate
---

### Description

cpuaff is a C++ library that abstracts CPU affinity settings for multiple platforms.  It is a header-only library on some platforms.  Other platforms are supported using [hwloc](http://www.open-mpi.org/projects/hwloc/).  The project aims to fully support all platforms as header-only eventually.

To see a list of supported platforms click [here](supported_platforms.html).

For a more detailed description of cpuaff, click [here](details.html)

### Releases

The latest release is [cpuaff-0.0.1](releases/cpuaff-0.0.1.tar.gz).  To get other releases, go to the [downloads](downloads.html) page.

For installation instructions, click [here](installation.html)

To get a snapshot of the repository, click one of the download links on this page.

### Rationale

Managing the CPU affinity of threads within a process is a powerful tool, but operating system provided interfaces are often difficult to use and hard to understand.  To this end, I have created cpuaff which will give an abstract view of the CPUs and PCI devices on a given machine.  The developer can then use this view to make intelligent decisions about setting thread CPU affinity.

### Licensing

cpuaff is distributed under the [New BSD](http://opensource.org/licenses/BSD-3-Clause) (or BSD 3-Clause) license.
