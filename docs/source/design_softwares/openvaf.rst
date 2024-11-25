OpenVAF
=======

Getting dependencies
--------------------
OpenVAF compilation requires Clang, LLVM, LD and Cargo. It is important to use the same version of Clang and LLVM.
With Ubuntu 24.04 we will get ``clang-18`` and ``llvm-18``.

.. code-block:: shell

    sudo apt install clang clang-tools llvm lld cargo


By default, the package manager might not link the right binary to the right command, and OpenVAF won't build.
For instance, the command ``clang-cl`` doesn't exist, but ``clang-cl-18`` does. So we need to create a link:

.. code-block:: shell
    
    sudo update-alternatives --install /usr/bin/clang-cl clang-cl /usr/bin/clang-cl-18 1

We need a recent version of rustc, to ensure this run:

.. code-block:: shell
    
    rustc --version

If the printed version is older 1.80, run and follow the command below to install a newer version:

.. code-block:: shell

    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh



Getting the sources
-------------------
Go in your ``tools_sources`` directory, to clone OpenVAF's sources.

Sadly `OpenVAF <https://github.com/pascalkuthe/OpenVAF>`_ stopped being officially maintained a year ago. And it is not
compatible anymore with recent LLVM/Clang versions. So we will need to use a fork compatible with LLVM 18. However, if
you are using LLVM 15 or 16, you can probably stick the original version.

.. code-block:: shell

    git clone https://github.com/Kreijstal/OpenVAF
    cd OpenVAF
    git switch llvm18reloaded

The ``git switch`` command allows us to use a different branch from the git repository.



OpenVAF compilation
-------------------

Warning: If you installed a particular version of ``rustc`` you will have to use the command ``cargo-1.80`` instead of
just ``cargo``.

Now we can start the compilation:

.. code-block:: shell

    cargo build



Install OpenVAF
---------------

We can copy the compiled binary and move it to our tools directory:

.. code-block:: shell

    mv target/debug/openvaf ~/microelectronics/tools/
    echo 'export PATH="$PATH:$HOME/microelectronics/tools/"' >> ~/.bashrc

Now that OpenVAF is installed, you can delete the build files in ``tools_sources``. Go in that folder then:

.. code-block:: shell

    rm -rf OpenVAF
