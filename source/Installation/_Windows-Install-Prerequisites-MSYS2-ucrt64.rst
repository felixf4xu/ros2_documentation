System setup
------------


Install MSYS2
^^^^^^^^^^^^^^^^^^

MSYS2 is a collection of tools and libraries for building, installing and running native Windows software.
It provides up-to-date native builds for clang, CPython, CMake, Meson, OpenSSL, zlib, just to name a few. 
Install it by following the installation instructions:

https://www.msys2.org/#installation

MSYS2 also provides a package management system called Pacman, which can be used to install some other developer tools.

MSYS2 provides several "environments", ucrt64 is used for the following instructions.

  .. image:: /Installation/images/msys2-command-prompt-ucrt64.png

.. note::
After the installation, make sure ``C:\msys64\clang64\bin`` is in the ``PATH`` environment variable.

Install a C++ compiler (for example, `Clang`)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Open a MSYS2 Command Prompt (for example, `MSYS2 MinGW Clang x64`) and type the following to install Clang via Pacman:


.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-clang $MINGW_PACKAGE_PREFIX-llvm $MINGW_PACKAGE_PREFIX-libc++

Make sure clang is installed correcty by running the following command:

.. code-block:: bash

   clang++ --version

Install CMake
^^^^^^^^^^^^^

Open a MSYS2 Command Prompt and type the following to install CMake:

.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-cmake $MINGW_PACKAGE_PREFIX-cmake-gui $MINGW_PACKAGE_PREFIX-ninja
   
Install OpenSSL
^^^^^^^^^^^^^^^

Open a MSYS2 Command Prompt and type the following to install OpenSSL:

.. code-block:: bash

  pacman -S $MINGW_PACKAGE_PREFIX-openssl

Install OpenCV
^^^^^^^^^^^^^^

Some of the examples require OpenCV to be installed.

Open a MSYS2 Command Prompt and type the following to install:

.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-opencv

Install dependencies
^^^^^^^^^^^^^^^^^^^^

.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-asio $MINGW_PACKAGE_PREFIX-bullet $MINGW_PACKAGE_PREFIX-cunit $MINGW_PACKAGE_PREFIX-eigen $MINGW_PACKAGE_PREFIX-tinyxml2
   pacman -S $MINGW_PACKAGE_PREFIX-eigen3 
   $MINGW_PACKAGE_PREFIX-atomic

Install additional prerequisites
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-cppcheck $MINGW_PACKAGE_PREFIX-curl 
   pacman -S bison git

Install Python
^^^^^^^^^^^^^^

Open a MSYS2 Command Prompt and type the following to install Python via Pacman:

.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-python

.. note::

   `MSYS2 MinGW Clang x64` will install Python in ``C:\msys64\clang64\bin\python.exe``, and the rest of the installation expects it to be there.

Install Python dependencies
^^^^^^^^^^^^^^^^^^^^^^^^^^^

First install pip and its dependency of setuptools:

.. code-block:: bash
   pacman -S $MINGW_PACKAGE_PREFIX-python-pip $MINGW_PACKAGE_PREFIX-expat

Install more python tools:

.. code-block:: bash
   
   pacman -S $MINGW_PACKAGE_PREFIX-python-coverage
   pacman -S $MINGW_PACKAGE_PREFIX-python-flake8
   pacman -S $MINGW_PACKAGE_PREFIX-python-mock
   pacman -S $MINGW_PACKAGE_PREFIX-mypy
   pacman -S $MINGW_PACKAGE_PREFIX-python-autopep8
   pacman -S $MINGW_PACKAGE_PREFIX-python-pydocstyle
   pacman -S $MINGW_PACKAGE_PREFIX-python-pytest
   pacman -S $MINGW_PACKAGE_PREFIX-python-pytest-cov
   pacman -S $MINGW_PACKAGE_PREFIX-python-pytest-mock
   pacman -S $MINGW_PACKAGE_PREFIX-python-pytest-runner


Install python libraries by `pacman` in MSYS2:

.. code-block:: bash
   pacman -S $MINGW_PACKAGE_PREFIX-python-cryptography  
   pacman -S $MINGW_PACKAGE_PREFIX-python-opencv  
   pacman -S $MINGW_PACKAGE_PREFIX-python-pyqt5
   pacman -S $MINGW_PACKAGE_PREFIX-python-pillow 
   pacman -S $MINGW_PACKAGE_PREFIX-python-psutil  
   pacman -S $MINGW_PACKAGE_PREFIX-python-cairo
   pacman -S $MINGW_PACKAGE_PREFIX-python-matplotlib 
   pacman -S $MINGW_PACKAGE_PREFIX-python-importlib-metadata 
   pacman -S $MINGW_PACKAGE_PREFIX-python-python-lark-parser
   pacman -S $MINGW_PACKAGE_PREFIX-python-lxml
   pacman -S $MINGW_PACKAGE_PREFIX-python-netifaces
   pacman -S $MINGW_PACKAGE_PREFIX-python-numpy
   pacman -S $MINGW_PACKAGE_PREFIX-python-yaml 
   pacman -S $MINGW_PACKAGE_PREFIX-python-pytest

Install build tools provided by pip:

.. code-block:: bash
   
   pip install -U vcstool rosdistro catkin_pkg
   pip install -U colcon-core colcon-cmake colcon-core colcon-defaults colcon-devtools colcon-library-path colcon-metadata
   pip install -U colcon-output colcon-package-information colcon-package-selection colcon-parallel-executor colcon-powershell    
   pip install -U colcon-python-setup-py colcon-recursive-crawl colcon-ros colcon-test-result

.. note::
   ``colcon-notification`` has installation issues in the MSYS2 environment. You can install it from source using pip and it's optional.

Now install some additional python dependencies:

.. code-block:: bash

   pip install -U pydot 

Install miscellaneous prerequisites
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Install xmllint (from libxml2):

.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-libxml2

* xmllint.exe is installed at ``C:\msys64\clang64\bin\xmllint.exe``.

Install Qt5
^^^^^^^^^^^

.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-qt5

.. code-block:: bash

   setx /m Qt5_DIR C:\Qt\Qt5.12.12\5.12.12\msvc2017_64
   setx /m QT_QPA_PLATFORM_PLUGIN_PATH C:\Qt\Qt5.12.12\5.12.12\msvc2017_64\plugins\platforms

RQt dependencies
^^^^^^^^^^^^^^^^

To run rqt_graph you need to install graphviz:

.. code-block:: bash

   pacman -S $MINGW_PACKAGE_PREFIX-graphviz

Make sure graphviz is working by running the following command:

.. code-block:: bash

   dot -V