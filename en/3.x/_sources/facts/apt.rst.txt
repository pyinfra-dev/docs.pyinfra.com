Apt Facts
---------

See also: :doc:`../operations/apt`.

.. _facts:apt.AptKeys:

:code:`apt.AptKeys`
~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(AptKeys, directories=None)

Returns information on GPG keys available to APT.

This fact reuses the GpgKeyrings infrastructure to search APT's modern keyring
directories instead of using the deprecated apt-key command. It provides
compatibility with the old AptKeys interface while leveraging the modern
GPG infrastructure.

.. code:: python

    {
        "3B4FE6ACC0B21F32": {
            "validity": "-",
            "length": 4096,
            "subkeys": {},
            "fingerprint": "790BC7277767219C42C86F933B4FE6ACC0B21F32",
            "uid_hash": "B7A02867A0C1D32B594B36C00E20C8C57E397748",
            "uid": "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
        },
    }


.. _facts:apt.AptSources:

:code:`apt.AptSources`
~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(AptSources)

Returns a list of installed apt sources (legacy .list + **deb822** .sources).

Returns a list of AptRepo instances that behave like dicts for backward compatibility:

    [AptRepo(type="deb", url="http://archive.ubuntu.org", ...)]

Each AptRepo can be accessed like a dict:
    repo['type']  # works like repo.type
    repo.get('url')  # works like getattr(repo, 'url')


.. _facts:apt.SimulateOperationWillChange:

:code:`apt.SimulateOperationWillChange`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(SimulateOperationWillChange, command)

Simulate an 'apt-get' operation and try to detect if any changes would be performed.

