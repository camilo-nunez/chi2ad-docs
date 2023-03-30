The `module` command
====================

Several software components (compiler, libraries, software, etc.) are already available on the Chi2AD cluster.

The `module` command allows you to customize your environment according to your usage by charging modules. Each loaded module updates your environment variables (such as your `\$PATH` variable) to make a software component reachable by your code.

Available modules
~~~~~~~~~~~~~~~~~

The `module avail` command lists all the available modules installed on Chi2AD cluster. Note that each module comes with its specific version.

.. code-block::

    [<uid>@chi2ad-headnode-01]% module avail
    ------------------------------------------ /opt/ohpc/pub/modulefiles -------------------------------------------
    EasyBuild/4.6.2      cmake/3.24.2    libfabric/1.13.0    prun/2.2             valgrind/3.19.0
    autotools            gnu12/12.2.0    os                  singularity/3.7.1
    charliecloud/0.15    hwloc/2.7.0     papi/6.0.0          ucx/1.11.2


Load a module
~~~~~~~~~~~~~

The `module load` command adds one or more modules to your current session.

.. code-block::

    [<uid>@chi2ad-headnode-01]% module load languages/anaconda3

List loaded modules
~~~~~~~~~~~~~~~~~~~

The `module list` command lists the modules which are currently loaded in your environment.

.. code-block:: console

    [<uid>@chi2ad-headnode-01]% module load valgrind
    [<uid>@chi2ad-headnode-01]% module list

    Currently Loaded Modules:
    1) singularity/3.7.1   2) valgrind/3.19.0

Unload a module
~~~~~~~~~~~~~~~

The `module unload`` option unloads a software component (make it unreachable by your environment by removing the proper paths from your environment variables).

.. code-block:: console

    [<uid>@chi2ad-headnode-01]% module list

    Currently Loaded Modules:
    1) singularity/3.7.1   2) valgrind/3.19.0

    [<uid>@chi2ad-headnode-01]% module unload singularity/3.7.1 
    [<uid>@chi2ad-headnode-01]% module list

    Currently Loaded Modules:
    1) valgrind/3.19.0