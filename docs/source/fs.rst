Data Management
===============

.. autosummary::
   :toctree: generated

   lumache

Filesystems
-----------

On Chi2AD, we provide the Lustre parallel filesystem version 2.10.5. Users have access to two different storage spaces: `HOME` and `WORK`. Each storage area has a specific purpose as described below.

+----------+-------------------------------------------------------------------------------------------------------------+
|| HOME    || is the file system where users sessions start upon login.                                                  |
||         || It is backed up and should be used to store shell setup files, source codes, scripts, and important files. |
+----------+-------------------------------------------------------------------------------------------------------------+
|| ARCHIVE || is a project space available through the allocations process and shared between all users of a project. It |
||         || provides disk space for large amounts of data, but it is not backed up. It can be used e.g. for writing    |
||         || raw model output and processing of data that is accessible to all project members.                         |
+----------+-------------------------------------------------------------------------------------------------------------+

The Lustre file system is available on all nodes (login and compute), so you can use them during interactive sessions and in batch jobs. The table below provides further details on the different storage spaces.

+----------------+---------------------------------------------------------------+---------------------------------------------------------+
| File System    | HOME                                                          | ARCHIVE                                                 |
+================+===============================================================+=========================================================+
| path           | `/users/<uid>`                                                | `/work/<projectid>`                                     |
+----------------+---------------------------------------------------------------+---------------------------------------------------------+
|| description   || Assigned to the user account.                                || Assigned to project account. Interim storage of output |
||               || Storage of personal settings files, source codes and scripts || from running applications and frequently accessed data |
+----------------+---------------------------------------------------------------+---------------------------------------------------------+
| quota          | 500 GB & 1.000.000 files                                      | according to project allocation                         |
+----------------+---------------------------------------------------------------+---------------------------------------------------------+

File Transfers
--------------

The files transfer from or to the file system `HOME` or `ARCHIVE` must be done through the server `login.hpc.chivo.cl`. This server is over the 10Gbps REUNA network.

.. attention::
    For the following two methods you must be enabled to use the SSH service.

Method I) `scp`
~~~~~~~~~~~~~~~

If you want to transfer files from your **local machine to your remote file system**, use the following command:

.. code-block:: console

    [client@localhost]% scp -r <local/folder> <uid>@ login.hpc.chivo.cl:~/<remote/folder>

If you want to transfer files from your **remote file system to local machine**, use the following command:

.. code-block:: console

    [client@localhost]% scp -r <uid>@login.hpc.chivo.cl:~/<remote/folder> <local/folder>

Method II) `rsync`
~~~~~~~~~~~~~~~~~~

If you want to transfer files from your **local machine to your remote file system**, use the following command:

.. code-block:: console

    [client@localhost]% rsync -rtlv --progress <local/folder> <uid>@login.hpc.chivo.cl:~/<remote/folder>

If you want to transfer files from your **remote file system to local machine**, use the following command:

.. code-block:: console

    [client@localhost]% rsync -rtlv --progress <uid>@login.hpc.chivo.cl:~/<remote/folder> <local/folder>