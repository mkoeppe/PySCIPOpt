Building the Python interface
=============================

The SCIP Python interface uses the shared library of the [SCIP Optimization Suite](http://scip.zib.de/).
Therefore you have to run

    make SHARED=true GMP=false READLINE=false scipoptlib

from the root of the SCIP Optimization Suite directory. This will result in the creation of the directory `<path/to/scipopt/lib>` and the shared library `libscipopt.so`. You may remove the `READLINE` and `GMP` flags if these tools are correctly installed in your environment.

From within the `PySCIPOpt` directory, please execute the following command:

    env SCIPOPTDIR=<path/to/scipopt> python setup.py install

You may use the additional options `--user` or `--prefix=<custom-python-path>`, to build the interface locally.

PySCIPOpt requires [Cython](http://cython.org/) to be installed in your system. If the Cython compilation fails, upgrade your Cython version (confirmed that version 0.20.1 fails). Furthermore, you need to have the Python development files installed on your system (error message "Python.h not found"):

    sudo apt-get install python-dev   # for Python 2
    sudo apt-get install python3-dev  # for Python 3


TROUBLESHOOTING
===============

The installation routine tries to generate symbolic links to the library directory `lib` as well as to the `src` directory of SCIP. In case of installation problems you should verify the correctness of the links in the directories `lib` and `include`.

Note:
-----

You cannot use the interface module from within the `PySCIPOpt` main directory. This is because Python will try to import the `pyscipopt` package from the local directory instead of using the installed one.

Currently, Windows is not officially supported. You are invited to submit a pull request for working setup routines.
