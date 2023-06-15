Utilization of GPU Services
===========================

.. attention::
    The following document is available only for users with GPU permissions in the cluster. Unauthorized access to the GPU servers is strictly prohibited and will result in account suspension.


Prior to reading the document, please ensure that you have reviewed the following sections:

.. toctree::

   access
   fs

Available GPU servers
~~~~~~~~~~~~~~~~~~~~~

+---------------------------------+---------------------------+---------------+-----------------------+
| hostname                        | CPU                       | GPUs          | memory                |
+=================================+===========================+===============+=======================+
| chi2ad-gpu-01.internal.chivo.cl | 1x Intel Xeon Silver 4310 | 1x NVIDIA A40 | 4x 1684MB 2133MHZ ECC |
+---------------------------------+---------------------------+---------------+-----------------------+

Available GPU servers
~~~~~~~~~~~~~~~~~~~~~
To access one of the GPU servers, first log in to the login node, and then proceed to log in to the GPU server using the following SSH command, replacing <iud> with your username:

.. code-block:: console

    [<uid>@chi2ad-login-01]% ssh chi2ad-gpu-01.internal.chivo.cl

Once inside the node, create or attached to your container.

NVIDIA Containers with Docker
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. warning::
    Please refrain from using any service other than Docker to run your environment. Specifically, avoid attempting to compile or execute your CUDA scripts outside of your Docker container.


How to run a `PyTorch` container environment
---------------------------------------------
For this section, we will use the official `PyTorch` container available for the `NVIDIA` catalog. For more information you can go `here <https://catalog.ngc.nvidia.com/orgs/nvidia/containers/pytorch>`_.

.. code-block:: console

    [<uid>@chi2ad-gpu-01]$ docker run -d --gpus all --ipc=host -p <your-port>:8888 -v ~/:/chi2ad nvcr.io/nvidia/pytorch:23.05-py3 jupyter lab --allow-root --ip='*' --port=8888 --no-browser --NotebookApp.token='' --NotebookApp.allow_origin='*' --notebook-dir=/chi2ad

where <your-port> must be an available private port. Does Not change the other flags and arguments from the command.

Then you can see if your container is running with the command:

.. code-block:: console

    [<uid>@chi2ad-gpu-01]$  docker ps
    CONTAINER ID   IMAGE                              COMMAND                  CREATED          STATUS         PORTS                                                 NAMES
    8515f1df23f0   nvcr.io/nvidia/pytorch:23.05-py3   "/opt/nvidia/nvidia_…"   11 seconds ago   Up 7 seconds   6006/tcp, 0.0.0.0:8889->8888/tcp, :::8889->8888/tcp   hungry_bhabha