Uv Operations
-------------


Operations for ``uv``:
    + install, remove or upgrade Python packages
    + install, remove or upgrade  'tools'
    + create or remove virtual environments (venv's)
    + ensure the uv tool executable directory is on the PATH


Facts used in these operations: :ref:`facts:files.File`, :ref:`facts:uv.UvInstalledPythonsByVersion`, :ref:`facts:uv.UvPipPackages`, :ref:`facts:uv.UvToolDir`, :ref:`facts:uv.UvTools`.

.. _operations:uv.packages:

:code:`uv.packages`
~~~~~~~~~~~~~~~~~~~

Install/remove/update Python packages using ``uv pip``

.. code:: python

    uv.packages(
         packages: 'str | list[str]',
         *,
         requirements: 'str | None' = None,
         present: 'bool' = True,
         latest: 'bool' = False,
         extra_args: 'str | list[str] | None' = None,
         **kwargs,
    )

+ **packages**: a package or list of packages to install/uninstall
+ **requirements**: optionally a path to a requirements file to install/uninstall. Default None.
+ **present**: whether the packages should be installed or uninstalled. Default True.
+ **latest**: whether to upgrade packages for which a version was not specified. Default False.
+ **extra_args**: zero or more additional arguments to the ``uv`` command. Default None.

Python Package versions:
    Package versions can be specified in the `usual manner`_, e.g. ``<pkg>==<version>``.

.. _usual manner: https://pip.pypa.io/en/stable/reference/requirement-specifiers/

**Example:**

.. code:: python

    uv.packages(
        name="Install Requests",
        packages=["requests"],
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:uv.pythons:

:code:`uv.pythons`
~~~~~~~~~~~~~~~~~~

Install/remove Python version(s).

.. code:: python

    uv.pythons(
         versions: 'str | list[str]',
         *,
         present: 'bool' = True,
         managed: 'bool' = True,
         extra_args: 'str | list[str] | None' = None,
         **kwargs,
    )

+ **version**: a version or list of Python versions
+ **present**: whether the versions should be installed or removed. Default True.
+ **managed**: whether only managed or all available version should be considered. Default True.
+ **extra_args**: zero or more additional arguments to be passed to ``uv``. Default None.

**Example:**

.. code:: python

    uv.pythons(
        name="Install Python 3.13 and 3.14",
        versions=["3.14", "3.13"],
        present=True
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:uv.tools:

:code:`uv.tools`
~~~~~~~~~~~~~~~~

Install/remove/update packages using ``uv tool``.

.. code:: python

    uv.tools(
         tools: 'str | list[str]',
         *,
         present: 'bool' = True,
         latest: 'bool' = False,
         extra_args: 'str | list[str] | None' = None,
         **kwargs,
    )

+ **tools**: a package or list of packages to install as tools
+ **present**: whether the packages should be installed or uninstalled.  Default True.
+ **latest**: whether or not to upgrade packages without a specified version. Default False.
+ **extra_args**: zero or more additional arguments to ``uv``. Default None.

Versions:
    Tool versions may be, but are not required to be, specified in the
    `usual manner`_: ``<pkg>==<version>``.

**Example:**

.. code:: python

    uv.tools(
        name="Install Pyinfra",
        tools=["pyinfra"],
        present=True
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:uv.tools_update_shell:

:code:`uv.tools_update_shell`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ensure that the ``uv`` tool executable directory is on the `PATH`.

.. code:: python

    uv.tools_update_shell**kwargs,    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:uv.tools_upgrade_all:

:code:`uv.tools_upgrade_all`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Upgrade all ``uv`` tools.

.. code:: python

    uv.tools_upgrade_all(*, extra_args: 'str | list[str] | None' = None,
         **kwargs,
    )

+ **extra_args**: zero or more additional arguments to ``uv``. Default None.

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:uv.venv:

:code:`uv.venv`
~~~~~~~~~~~~~~~

Add/remove a Python venv in the specified location.

.. code:: python

    uv.venv(
         path: 'str',
         *,
         present: 'bool' = True,
         python: 'str | None' = None,
         allow_existing: 'bool' = False,
         clear_existing: 'bool' = False,
         link_mode: "Literal['clone', 'copy', 'hardlink', 'symlink'] | None" = None,
         seed: 'bool' = False,
         site_packages: 'bool' = False,
         extra_args: 'str | list[str] | None' = None,
         **kwargs,
    )

+ **path**: where to create the venv
+ **present**: whether the venv should be created or removed.  Default True
+ **python**: Python interpreter to use. Defaults to not specified.
+ **allow_existing**: allow (and retain) existing files in the venv directory. Default False
+ **clear_existing**: remove all existing files in the venv directory. Default False
+ **seed**: whether to seed the venv with ``pip``, and pre-3.12, ``setuptools`` and ``wheel``.
  Default False
+ **site_packages**: give the venv access to the global site-packages. Default False
+ **link_mode**: method to use when installing seed packages: clone, copy, hardlink or symlink.
  Default is platform-dependent
+ **extra_args**: zero or more additional arguments to the `'uv`' command

**Example:**

.. code:: python

    uv.venv(
        name="Create a venv",
        path="/my/projects/useful-project/.venv",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.

