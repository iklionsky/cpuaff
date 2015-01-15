---
title: cpuaff
layout: slate
---

### Description

cpuaff is a C++ library that abstracts CPU affinity settings for multiple platforms.  It is a header-only library on some platforms.  Other platforms are supported using [hwloc](http://www.open-mpi.org/projects/hwloc/).  The project aims to fully support all platforms as header-only eventually.

To see a list of supported platforms [click here](supported_platforms.html).

### Releases

The latest release is [cpuaff-0.0.1](releases/cpuaff-0.0.1.tar.gz).  To get other releases, go to the [downloads](downloads.html) page.

For installation instructions, [click here](installation.html)

To get a snapshot of the repository, click one of the download links on this page.

### Details

cpuaff builds up a four part view of every processor on a system.  CPUs are identified by their socket, core, and processing_unit.  Additionally, each cpu on the system has a notion of its NUMA node.  cpuaff also builds a view of the PCI devices on the system and the CPUs that are local to them.  Currently PCI mapping is only available on Linux, but the goal is to implement it for every platform to give the developer maximum flexibility in selecting the proper CPU affinities for his/her process.

cpuaff aims to eventually be completely header-only for easy integration into existing systems.  For the time being the Linux implementation is header-only.  Other platforms are implemented using [hwloc](http://www.open-mpi.org/projects/hwloc/) as an interface to the underlying hardware so executables must link to [hwloc](http://www.open-mpi.org/projects/hwloc/).

### Rationale

Managing the CPU affinity of threads within a process is a powerful tool, but operating system provided interfaces are often difficult to use and hard to understand.  To this end, I have created cpuaff which will give an abstract view of the CPUs and PCI devices on a given machine.  The developer can then use this view to make intelligent decisions about setting thread CPU affinity.

### Licensing

cpuaff is distributed under the [New BSD](http://opensource.org/licenses/BSD-3-Clause) (or BSD 3-Clause) license.
