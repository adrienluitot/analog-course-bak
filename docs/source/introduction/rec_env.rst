Recommended Environment
=======================

.. list-table:: Recommended Environment
  :widths: 50 50
  :header-rows: 0

  * - Operating System
    - Ubuntu 24.04
  * - Storage
    - 30 GB
  * - Memory
    - 4 GB
  * - Python Version
    - 3.12


Operating System
----------------

Analog design is doable with any operating system, but it is easier to do it on Linux. On this course we will mostly
consider Linux for the moment, more particularly Ubuntu 24.04 (LTS).

.. note::
  *Why Ubuntu 24.04 LTS ?* There are several reasons to this. For Ubuntu, it is basically the most known Linux operating
  system, meaning there are already a lot of tutorials, packages and resources around. The version 24.04 is one of the 
  latest versions by the time we write this course. And it is an LTS (Long Term Support) version, so it should help
  to make this tutorial usable for a longer time.

If you are not using Ubuntu, but still using Linux, everything should be similar. If you are not using Linux, you can
still try follow the course with your system, or you can install Ubuntu or Linux on your computer, a server or a virtual
machine. We won't cover the installation of Linux, there are already a plethora of tutorials on the internet.

Anyway, the main differences will happend when installing the EDA tools, which have their own installation tutorials on
the internet. Once you have installed the tools, everything should be almost the same.



Files Organisation
------------------

Organisation is very important in order to be more efficient. In our case, respecting a simple but well done file 
organisation will simplifies the installation and usage of the different tools. You are obviously free to organise your
files as desired. But we will consider the that you use our organisation, if not you will have to adapt.

Here is how we organise our files:

.. code-block::

  microelectronics/
  ├─ PDK/
  │  ├─ IHP/
  │  |  ├─ IHP-Open-PDK/
  │  |  ├─ ...
  |  ├─ ...
  ├─ tools/
  │  ├─  ...
  ├─ tools_sources/
  │  ├─ ...
  ├─ projects/
  │  ├─ LNA/
  │  |   ├─ ...

**microelectronics/** is the root directory, where everything related to our design will be stored.

**PDK/** will store all the PDK we have, it's generally a good idea to have them all in one place. This folder is
sorted by foundries, even if this course only focus on IHP's PDK, we could have more. Also we might have several 
technologies of one foundry, thus several PDK, it's why we gather them by foundry.

**tools/** will contains the tools that we cannot find in the repositories of our operating system. There will be 
binaries, but also scripts.

**tools_sources/** will be used to build tools. Sometimes we cannot find the tools in repositories nor download the
binaries. Therefore we will need to get the sources of the tool and build it. To keep everything clean, we will use this
directory.

Finally, **projects/** will gather our projects. In the course we will only have a LNA.

Python version
--------------

Ubuntu 24.04 has python 3.12 installed by default, it is also the recommended version. Newer versions should work
however.
