Xbps Facts
----------

See also: :doc:`../operations/xbps`.

.. _facts:xbps.XbpsPackages:

:code:`xbps.XbpsPackages`
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(XbpsPackages)

Returns a dict of installed XBPS packages:

.. code:: python

    {
        "package_name": ["version"],
    }

