Ngspice
=======

From verison 44, ngspice is compatible with OSDI v0.4, so it might be interesting to use it. However it is not yet
available on package managers, so we have to build it.

Getting dependencies
--------------------

.. code-block:: shell

    sudo apt install autoconf libtool automake libxaw7-dev libreadline-dev


Downloading the sources
-----------------------

.. code-block:: shell

    git clone https://github.com/imr/ngspice
    cd ngspice
    git switch pre-master-44


Compiling
---------

.. code-block:: shell

    ./autogen.sh
    mkdir release && cd release
    ../configure --with-x --enable-cider --enable-predictor 
    make 2>&1 | tee make.log


Installing
----------

.. code-block:: shell

    sudo make install


Cleaning workspace
------------------

You can now delete the ngspice folder located in ``tools_sources``