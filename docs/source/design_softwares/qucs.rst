QUCS
====

To create and design our schematic circuit, the Quite Universal Circuit Simulator (QUCS) will be used. Also, for this project, the usage of free circuit simulation kernels is adviced.
Thus, we will use the Qucs-S extension with Ngspice as simulation kernel. 

Installation
------------

You can install the dependencies via the following command :

.. code-block:: python

    sudo apt-get install ngspice build-essential git cmake qtbase5-dev qttools5-dev libqt5svg5-dev libqt5charts5-dev flex bison gperf dos2unix

You can visit the `Qucs-S GitHub <https://github.com/ra3xdh/qucs_s>`_ for more information.

.. note::
    Make sure to install the dependencies required for the installation.

Setup & Configuration
---------------------

Include the PDK in Qucs-S
^^^^^^^^^^^^^^^^^^^^^^^^^

FOR IHP SG13G2 PDK
^^^^^^^^^^^^^^^^^^
Run the following commands : 

.. code-block:: shell

    cd IHP-Open-PDK-main/ihp-sg13g2/libs.tech/qucs
    ./install.py

Usage
-----

Create a schematic
^^^^^^^^^^^^^^^^^^

tbd

Add simulation parameters
^^^^^^^^^^^^^^^^^^^^^^^^^

tbd

Start a simulation
^^^^^^^^^^^^^^^^^^

tbd

Plotting results
^^^^^^^^^^^^^^^^

tbd