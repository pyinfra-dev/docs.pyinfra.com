Pkgin Facts
-----------

See also: :doc:`../operations/pkgin`.

.. _facts:pkgin.PkginPackages:

:code:`pkgin.PkginPackages`
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(PkginPackages)

Returns a dict of installed pkgin packages:

.. code:: python

    {
        "package_name": ["version"],
    }

