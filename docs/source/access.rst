Access to the Cluster
=====================

Login
~~~~~
You can log into Chi2AD with the following ssh command, replacing `<uid>` with your username:

.. code-block::

    [client@localhost]% ssh login.hpc.chivo.cl -l <uid>

After having logged into Chi2AD, you will find yourself on the login node `chi2ad-login-01`. The login node serve as the front ends to the compute nodes of the HPC cluster. They are intended for the editing and compilation of source code files.

Login Shell
~~~~~~~~~~~
The default login shell for new Chi2AD users is `bash`. A login bash shell looks for `.bash_profile`, `.bash_login` or `.profile`` in your home directory and executes commands from the first file found. A non-login bash shell or bash subshell reads `.bashrc` file.

Headnode
~~~~~~~~
In the headnode (A.K.A. `chi2ad-headnode-01`), the users can interact with the cluster. You can log into the `chi2ad-headnode-01` with the following ssh command:

.. code-block::

    [<uid>@chi2ad-login-01]% ssh chi2ad-headnode-01.internal.chivo.cl

The typical tasks and settings that can be put in the shell setup files are for example:

* Creation of a custom prompt
* Modification of search path for external commands and programs
* Definition of environment variables needed by programs or scripts
* Definition of aliases
* Execution of commands (e.g. `module load <modname>/<version>`).

.. warning::
    Never run your customs scripts or compute scripts in the headnode.

Interactive shell on Compute Node
---------------------------------
If you need an interactive bash session on a compute node, you need to run the following command in the `chi2ad-headnode-01`:

.. code-block::

    [<uid>@chi2ad-headnode-01]% srun -p compute-node-A --time=HH:MM:SS --mem=nnG --pty bash

where `HH:MM:SS` are hours, minutes and seconds, and `nnG` are the memory in gigabytes to allocate (10G, 32G, etc.).

Close the shell when you are done. If you don’t, the process will keep running until your time limit. All of this time will be counted against your usage.

Useful Lustre Commands
~~~~~~~~~~~~~~~~~~~~~~
A Lustre filesystem is a high-performance shared filesystem for Linux clusters that is managed with Lustre software. It is highly scalable and can support many thousands of client nodes, petabytes of storage, and hundreds of gigabytes per second of I/O throughput.

Viewing Striping Information
----------------------------
To view the striping information for a specific file or directory:

.. code-block::

    [<uid>@chi2ad-login-01]% lfs getstripe filename
    [<uid>@chi2ad-login-01]% lfs getstripe -d directory_name

Omitting the -d flag will display striping for all files in the directory.

Listing Disk Usage and Quotas
-----------------------------
To display disk usage and limits on your `/users/<uid>` directory:

.. code-block::

    [<uid>@chi2ad-login-01]% lfs quota -h -u <uid> /users

or

.. code-block::
    
    [<uid>@chi2ad-login-01]% lfs quota -h -u <uid> /users/<uid>

To display usage on each OST, add the -v option:

.. code-block::

    [<uid>@chi2ad-login-01]% lfs quota -h -v -u <uid> /users/<uid>

Listing Space Usage
-------------------
To list space usage per OST and MDT, in human-readable format, for all Lustre filesystems or for a specific one:

.. code-block::

    [<uid>@chi2ad-login-01]% lfs df -h
    [<uid>@chi2ad-login-01]% lfs df -h /users
    [<uid>@chi2ad-login-01]% lfs df -h /work