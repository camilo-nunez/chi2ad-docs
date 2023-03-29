Data Management - Filesystems
=============================

.. autosummary::
   :toctree: generated

   lumache

On Chi2AD, we provide the Lustre parallel filesystem version 2.10.5. Users have access to three different storage spaces: `HOME` and `WORK`. Each storage area has a specific purpose as described below.

+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|  HOME   |                                                                 is the file system where users sessions start upon login. It is backed up and should be used to store shell setup files, source codes, scripts, and important files.                                                                  |
+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ARCHIVE | is a project space available through the allocations process and shared between all users of a project. It provides disk space for large amounts of data, but it is not backed up. It can be used e.g. for writing raw model output and processing of data that is accessible to all project members. |
+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The Lustre file system is available on all nodes (login and compute), so you can use them during interactive sessions and in batch jobs. The table below provides further details on the different storage spaces.

+-----------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| File System     | HOME                                                                                        | ARCHIVE                                                                                                        |
+=================+=============================================================================================+================================================================================================================+
| path            | `/users/<uid>`                                                                              | `/work/<projectid>`                                                                                            |
+-----------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| description     | Assigned to the user account. Storage of personal settings files, source codes and scripts  | Assigned to project account. Interim storage of output from running applications and frequently accessed data  |
+-----------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| quota           | 500 GB & 1.000.000 files                                                                    | according to project allocation                                                                                |
+-----------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| data life time  | until user account deletion                                                                 | 1 month after project expiration                                                                               |
+-----------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+