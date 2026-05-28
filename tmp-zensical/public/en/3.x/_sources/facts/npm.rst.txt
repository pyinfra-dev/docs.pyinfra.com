Npm Facts
---------

See also: :doc:`../operations/npm`.

.. _facts:npm.NpmPackages:

:code:`npm.NpmPackages`
~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(NpmPackages, directory=None)

Returns a dict of installed npm packages globally or in a given directory:

.. code:: python

    {
        "package_name": ["version"],
    }

