Dnf Facts
---------

See also: :doc:`../operations/dnf`.

.. _facts:dnf.DnfDisabledModules:

:code:`dnf.DnfDisabledModules`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DnfDisabledModules)

Returns a sorted list of dnf module names that have been explicitly disabled:

.. code:: python

    ["ruby", "php"]


.. _facts:dnf.DnfEnabledModules:

:code:`dnf.DnfEnabledModules`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DnfEnabledModules)

Returns a dict mapping enabled dnf module names to their enabled stream:

.. code:: python

    {
        "postgresql": "16",
        "nodejs": "20",
    }


.. _facts:dnf.DnfRepositories:

:code:`dnf.DnfRepositories`
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DnfRepositories)

Returns a list of installed dnf repositories:

.. code:: python

    [
        {
            "repoid": "baseos",
            "name": "AlmaLinux $releasever - BaseOS",
            "mirrorlist": "https://mirrors.almalinux.org/mirrorlist/$releasever/baseos",
            "enabled": "1",
            "gpgcheck": "1",
            "countme": "1",
            "gpgkey": "file:///etc/pki/rpm-gpg/RPM-GPG-KEY-AlmaLinux-9",
            "metadata_expire": "86400",
            "enabled_metadata": "1",
            "filename": "/etc/yum.repos.d/almalinux.repo"
        },
    ]

