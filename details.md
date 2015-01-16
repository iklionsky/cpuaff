---
title: Details
layout: slate
---

### Rationale

Managing the CPU affinity of threads within a process is a powerful tool, but operating system provided interfaces are often difficult to use and hard to understand.  To this end, I have created cpuaff which will give an abstract view of the CPUs and PCI devices on a given machine.  The developer can then use this view to make intelligent decisions about setting thread CPU affinity.

### Description

cpuaff identifies CPUs by their socket, core, and processing unit.  Sockets are zero indexed.  Cores are zero indexed per socket.  Processing units are zero indexed per core.  CPUs are uniquely identified by an ordered triple of integers (socket, core, processing unit).  So the first processing unit on the third core of the first socket is represented by (0, 2, 0).  CPUs are also annotated with their NUMA node.

cpuaff also identifies PCI devices on the system.  They are identified uniquely by a platform specific address.  They can also be looked up by their vendor and device identifiers (each a 16 bit integer).  If the architecture supports it, PCI devices are annotated with their NUMA node.

Together this gives the user the power to select the appropriate CPU or CPUs to run a thread on.  For example, if one has a PCI device on NUMA node 0, it is advantageous to run code that interfaces with the device on CPUs from the same NUMA node.  cpuaff makes this simple using an affinity\_manager.  The affinity\_manager loads all the CPUs and PCI devices on a system and allows the user to query them in a variety of ways.  The user can then call the get\_affinity() and set\_affinity() member functions of the affinity\_manager class to get or set thread affinity.

Currently, cpuaff fully supports Linux via sysfs.  Other platforms are partially supported using [hwloc](http://www.open-mpi.org/projects/hwloc).  Unfortunately [hwloc](http://www.open-mpi.org/projects/hwloc) does not have support for finding CPUs local to PCI devices so PCI mapping is not supported.  One of the goals of this project is to fully implement both CPU affinity and PCI mapping on all platforms without reliance on external libraries.
