Uv Facts
--------


Present information provided by ``uv``:
    + available and installed versions of Python
    + installed Python packages and their versions
    + where the installed versions of Python are stored
    + where `tools are installed`
    + version of ``uv`` available


See https://docs.astral.sh/uv/ for details of ``uv``

See also: :doc:`../operations/uv`.

.. _facts:uv.UvAvailablePythonsByImplementation:

:code:`uv.UvAvailablePythonsByImplementation`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvAvailablePythonsByImplementation, is_managed=True)

Provides the implementation(s) of Python available for installation along with the versions(s)
of the implementation(s).

    + **is_managed**: if set, only list Python implementations managed by `uv`. Default True

**Example:**

.. code:: python

    {
        "cpython-3.13.4-macos-aarch64-none": ["3.13.4"]
    }


.. _facts:uv.UvAvailablePythonsByVersion:

:code:`uv.UvAvailablePythonsByVersion`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvAvailablePythonsByVersion, is_managed=True)

Provides the version(s) of Python available for installation along with the implementation(s)
of the version(s).

    + **is_managed**: if set, only list Python implementations managed by `uv`. Default True

**Example:**

.. code:: python

    {
        "3.13.4": ["cpython-3.13.4-macos-aarch64-none"]
    }


.. _facts:uv.UvInstalledPythonsByImplementation:

:code:`uv.UvInstalledPythonsByImplementation`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvInstalledPythonsByImplementation, is_managed=True)

Provides the installed implementation(s) of Python along with the versions(s) of
the implementation(s).

    + **is_managed**: if set, only list Python implementations managed by `uv`. Default True

**Example:**

.. code:: python

    {
        "cpython-3.13.4-macos-aarch64-none": ["3.13.4"]
    }


.. _facts:uv.UvInstalledPythonsByVersion:

:code:`uv.UvInstalledPythonsByVersion`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvInstalledPythonsByVersion, is_managed=True)

Provides the installed versions of Python along with the implementation(s) of
the version(s).

    + **is_managed**: if set, only list Python versions managed by `uv`. Default True

**Example:**

.. code:: python

    {
        "3.13.4": ["cpython-3.13.4-macos-aarch64-none"]
    }


.. _facts:uv.UvPipPackages:

:code:`uv.UvPipPackages`
~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvPipPackages)

Provides the installed Python packages and their version.

**Example:**

.. code:: python

    {
        "requests": ["2.32.5"],
    }


.. _facts:uv.UvPythonDir:

:code:`uv.UvPythonDir`
~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvPythonDir)

Provides the directory in which uv installs Python implementations.

**Example:**

.. code:: python

    /home/someone/.local/share/uv/python


.. _facts:uv.UvToolDir:

:code:`uv.UvToolDir`
~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvToolDir)

Provides the directory in which uv installs tools.

**Example:**

.. code:: python

    /home/someone/.local/share/uv/tools


.. _facts:uv.UvTools:

:code:`uv.UvTools`
~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvTools)

Provides the tool(s) currently installed along with their version(s).

**Example:**

.. code:: python

    {
        "pyinfra": "3.4.1"
    }


.. _facts:uv.UvVersion:

:code:`uv.UvVersion`
~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(UvVersion)

Provides the version of uv installed.

**Example:**

.. code:: python

    uv 0.8.5 (Homebrew 2025-08-05)

