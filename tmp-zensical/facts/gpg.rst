Gpg Facts
---------

See also: :doc:`../operations/gpg`.

.. _facts:gpg.GpgKey:

:code:`gpg.GpgKey`
~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GpgKey, src)

Returns information on one or more GPG keys found in a file or URL.

.. code:: python

    {
        "KEY-ID": {
            "length": 4096,
            "uid": "Oxygem <hello@oxygem.com>"
        },
    }


.. _facts:gpg.GpgKeyrings:

:code:`gpg.GpgKeyrings`
~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GpgKeyrings, directories)

Returns information on all GPG keyrings found in specified directories.

.. code:: python

    {
        "/etc/apt/keyrings/docker.gpg": {
            "format": "gpg",
            "keys": {...}  # Same format as GpgKeys fact
        }
    }


.. _facts:gpg.GpgKeys:

:code:`gpg.GpgKeys`
~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GpgKeys, keyring=None)

Returns information on all public keys in a keychain.

.. code:: python

    {
        "KEY-ID": {
            "length": 4096,
            "uid": "Oxygem <hello@oxygem.com>"
        },
    }


.. _facts:gpg.GpgSecretKeys:

:code:`gpg.GpgSecretKeys`
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GpgSecretKeys, keyring=None)

Returns information on all secret keys in a keychain.

.. code:: python

    {
        "KEY-ID": {
            "length": 4096,
            "fingerprint": "ABC",
            "uid": "Oxygem <hello@oxygem.com>"
        },
    }

