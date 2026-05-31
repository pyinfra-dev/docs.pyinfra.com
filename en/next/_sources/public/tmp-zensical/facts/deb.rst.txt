Deb Facts
---------

.. _facts:deb.DebArch:

:code:`deb.DebArch`
~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DebArch)

Returns the architecture string used in apt repository sources, eg ``amd64``.


.. _facts:deb.DebPackage:

:code:`deb.DebPackage`
~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DebPackage, package)

Returns information on a .deb archive or installed package.


.. _facts:deb.DebPackages:

:code:`deb.DebPackages`
~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DebPackages)

Returns a dict of installed dpkg packages:

.. code:: python

    {
        "package_name": ["version"],
    }

