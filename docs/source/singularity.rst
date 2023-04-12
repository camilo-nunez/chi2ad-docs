`Singularity` containers
========================

How to load `Singularity` module in a compute node
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Search the `Singularity` module:

.. code-block:: console

    [<uid>@chi2ad-node-0XX]$ module avail

    -------------------- /opt/ohpc/pub/modulefiles -----------
    EasyBuild/4.6.2      gnu12/12.2.0        papi/6.0.0           valgrind/3.19.0
    autotools            hwloc/2.7.0         prun/2.2
    charliecloud/0.15    libfabric/1.13.0    singularity/3.7.1
    cmake/3.24.2         os                  ucx/1.11.2

Then select the available version for `Singularity`:

.. code-block:: console

    [<uid>@chi2ad-node-0XX]$ module load singularity

How to test a `Singularity`'s container
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

First, download the basic `hello-world` container from the `Singularity Hub`:

.. code-block:: console

    [<uid>@chi2ad-node-0XX]$ singularity pull shub://vsoch/hello-world


Finally, run the container with:

.. code-block:: console

    [<uid>@chi2ad-node-0XX]$ singularity run hello-world_latest.sif 
    RaawwWWWWWRRRR!! Avocado!

the output of the container must be `RaawwWWWWWRRRR!! Avocado!`.

How use CASA container
~~~~~~~~~~~~~~~~~~~~~~

Load the module in the allocated node:

.. code-block:: console

    [<uid>@chi2ad-node-0XX]$ module load singularity

Pull the last version of the CASA container:

.. code-block:: console

    [<uid>@chi2ad-node-0XX]$ singularity pull --arch amd64 library://camilo-nunez-fernandez/cassaca/casa:6.5.3

Run the IPython interactive shell:

.. code-block:: console

    [<uid>@chi2ad-node-0XX]$ singularity run casa_6.5.3.sif