QUCS
====

To create and design our schematic circuit, the Quite Universal Circuit Simulator (QUCS) will be used. Also, for this
project, the usage of free circuit simulation kernels is adviced. Thus, we will use the Qucs-S extension with Ngspice 
and Xyce as simulation kernels. 

In addition to this section, you can visit `Qucs-S GitHub <https://github.com/ra3xdh/qucs_s>`_ for more information.


Installation
------------

From repositories
^^^^^^^^^^^^^^^^^

The best way to get and maintain Qucs-S on Ubuntu is with the ``apt`` package manager. But Qucs-S is not directly on the
default Ubuntu's repositories, therefore we need to follow the procedure recommended by the tool's author. We describe
the procedure for Ubuntu 24.04 below, but you can also find it for other operating systems and version on `this website
<https://software.opensuse.org/download.html?project=home%3Ara3xdh&package=qucs-s>`_.

.. code-block:: shell

    echo 'deb http://download.opensuse.org/repositories/home:/ra3xdh/xUbuntu_24.04/ /' | sudo tee /etc/apt/sources.list.d/home:ra3xdh.list
    curl -fsSL https://download.opensuse.org/repositories/home:ra3xdh/xUbuntu_24.04/Release.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/home_ra3xdh.gpg > /dev/null
    sudo apt update
    sudo apt install qucs-s


From sources
^^^^^^^^^^^^

Another way to get Qucs-S is by building it from source. You can skip this part if you already installed the tool from
repositories.

Dependencies
""""""""""""

First, we need to make sure we have all the dependencies:

.. code-block:: shell

    sudo apt install cmake flex bison gperf dos2unix build-essential qt6-base-dev qt6-tools-dev qt6-tools-dev-tools libglx-dev linguist-qt6 qt6-l10n-tools libqt6svg6-dev libqt6-charts6-dev libgl1-mesa-dev

Getting the sources
"""""""""""""""""""

Now we can get the sources from GitHub, go at the address `<https://github.com/ra3xdh/qucs_s/releases>`_ and download
the file ``.tar.gz`` file corresponding to the version you want to install. Here we will use the version ``24.4.1``.
Move the downloaded file to your the ``tools_sources`` directory to keep things clean.


Builing and installing Qucs-S
"""""""""""""""""""""""""""""

First unarchive the sources and create a temporary build directory:

.. code-block:: shell

    tar xvfz qucs-s-24.4.1.tar.gz
    cd qucs-s-24.4.1
    mkdir builddir
    cd builddir

Then we prepare our build to install in the right folder. Adapt the ``CMAKE_INSTALL_PREFIX`` parameter to your file
organisation.

.. code-block:: shell

    cmake ..  -DCMAKE_INSTALL_PREFIX=../../../tools -DWITH_QT6=ON

After that we can build Qucs-S (This step might take some time):

.. code-block:: shell

    make

And finally install it:

.. code-block:: shell

    make install


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