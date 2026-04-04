Brew Facts
----------

See also: :doc:`../operations/brew`.

.. _facts:brew.BrewCasks:

:code:`brew.BrewCasks`
~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(BrewCasks)

Returns a dict of installed brew casks:

.. code:: python

    {
        "package_name": ["version"],
    }


.. _facts:brew.BrewPackages:

:code:`brew.BrewPackages`
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(BrewPackages)

Returns a dict of installed brew packages:

.. code:: python

    {
        "package_name": ["version"],
    }


.. _facts:brew.BrewTaps:

:code:`brew.BrewTaps`
~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(BrewTaps)

Returns a list of brew taps.


.. _facts:brew.BrewVersion:

:code:`brew.BrewVersion`
~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(BrewVersion)

Returns the version of brew installed as a semantic versioning tuple:

.. code:: python

    [major, minor, patch]

