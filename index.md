---
title: Home
layout: slate
---

### News

##### Continuous Integration and Some Minor Enhancements

Thanks to [Dirk Eddelbuettel](https://github.com/eddelbuettel) we now have continuous integration using [Travis CI](https://travis-ci.org).  As a result we now compile with clang as well as g++.  There were a few minor code enhancements that went in as part of this process but nothing worthy of a new release.

For the next release I plan to disentangle PCI device mapping from the affinity_manager class to make things more modular both for testing and usage.

2015-02-01 18:16:00

##### Version 0.0.1 Released

Released [cpuaff-0.0.1](releases/cpuaff-0.0.1.tar.gz).  All the code is there.  Unit tests using [CATCH](https://github.com/philsquared/Catch) are present.  Several examples exist as well.  Hooray!

More documentation as well as some examples on the website are in the works and will be released soon.

2015-01-25 15:08:00

### Description

cpuaff is a C++ library that abstracts CPU affinity settings for multiple platforms.  It is a header-only library on some platforms.  Other platforms are supported using [hwloc](http://www.open-mpi.org/projects/hwloc/).  The project aims to fully support all platforms as header-only eventually.

For a more detailed description of cpuaff, click [here](details.html)

To see a list of supported platforms click [here](supported_platforms.html).

### Releases

The latest release is [cpuaff-0.0.1](releases/cpuaff-0.0.1.tar.gz).  To get other releases, go to the [downloads](downloads.html) page.

For installation instructions, click [here](installation.html)

To get a snapshot of the repository, click one of the download links on this page.

### Simple Example

    #include <cpuaff/cpuaff.hpp>
    #include <iostream>
    
    int main(int argc, char *argv[])
    {
        cpuaff::affinity_manager manager;
    
        if (manager.has_cpus())
        {
            cpuaff::cpu_set cpus;
            manager.get_affinity(cpus);
    
            std::cout << "Initial Affinity:" << std::endl;
    
            cpuaff::cpu_set::iterator i = cpus.begin();
            cpuaff::cpu_set::iterator iend = cpus.end();
    
            for (; i != iend; ++i)
            {
                std::cout << "  " << (*i) << std::endl;
            }
    
            std::cout << std::endl;
    
            // set the affinity to all the processing units on
            // the first core
            cpuaff::cpu_set core_0;
            manager.get_cpus_by_core(core_0, 0);
    
            manager.set_affinity(core_0);
            manager.get_affinity(cpus);
    
            std::cout << "Affinity After Calling set_affinity():"
                      << std::endl;
            i = cpus.begin();
            iend = cpus.end();
    
            for (; i != iend; ++i)
            {
                std::cout << "  " << (*i) << std::endl;
            }
    
            return 0;
        }
    
        std::cerr << "cpuaff: unable to load cpus." << std::endl;
        return -1;
    }

### Pronunciation

Due to popular demand, we now have a guide on pronunciation.  cpuaff is pronounced "spoof" because all other pronunciations I have come up with sound like garbled French.

### Licensing

cpuaff is distributed under the [New BSD](http://opensource.org/licenses/BSD-3-Clause) (or BSD 3-Clause) license.
