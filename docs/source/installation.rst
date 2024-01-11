Installation
============

.. _installation:

CLI & Python Library
--------------------
The CLI and/or the Python library of Knew Karma can be installed directly from `PyPI <https://pypi.org/project/knewkarma>`_ with pip:


.. code-block:: console

    pip install knewkarma

.. note::

    This assumes Python 3.10 or later is installed on your system.

Building a Docker Container
---------------------------

.. important::

    Ensure you have cloned the project and have the Docker Engine/Daemon running on your system.

1. Move to the cloned *knewkarma* directory:

.. code-block:: console

    cd knewkarma

2. Build the Docker container:

.. code-block:: console

    docker build -t my-knewkarma-container .

GUI
---
The GUI instance of Knew Karma is only available for Windows systems, and can be installed by doing the following:

1. Download the latest setup files from the `releases page <https://github.com/bellingcat/knewkarma/releases/latest>`_.
2. Extract the zip file and find `KnewKarmaSetup.msi` and `setup.exe`.
3. Run the `setup.exe` file if you do not have the .NET Desktop Runtime installed, otherwise run the `KnewKarmaSetup.msi`.
4. Follow the on-screen instructions.

.. note::

    This installs Knew Karma and creates desktop and app menu shortcuts.
