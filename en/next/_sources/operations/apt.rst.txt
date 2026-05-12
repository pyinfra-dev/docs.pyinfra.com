Apt Operations
--------------


Manage apt packages and repositories.


Facts used in these operations: :ref:`facts:apt.AptSources`, :ref:`facts:server.Date`, :ref:`facts:deb.DebPackage`, :ref:`facts:deb.DebPackages`, :ref:`facts:files.File`, :ref:`facts:apt.SimulateOperationWillChange`.

.. _operations:apt.deb:

:code:`apt.deb`
~~~~~~~~~~~~~~~

Add/remove ``.deb`` file packages.

.. code:: python

    apt.deb(src: 'str', present=True, force=False,
         **kwargs,
    )

+ **src**: filename or URL of the ``.deb`` file
+ **present**: whether or not the package should exist on the system
+ **force**: whether to force the package install by passing `--force-yes` to apt

Note:
    When installing, ``apt-get install -f`` will be run to install any unmet
    dependencies.

URL sources with ``present=False``:
    If the ``.deb`` file isn't downloaded, pyinfra can't remove any existing
    package as the file won't exist until mid-deploy.

**Example:**

.. code:: python

    # Note: Assumes wget is installed.
    apt.deb(
        name="Install Chrome via deb",
        src="https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:apt.dist_upgrade:

:code:`apt.dist_upgrade`
~~~~~~~~~~~~~~~~~~~~~~~~

Updates all apt packages, employing dist-upgrade.

.. code:: python

    apt.dist_upgrade(auto_remove: 'bool' = False,
         **kwargs,
    )

+ **auto_remove**: removes transitive dependencies that are no longer needed.

**Example:**

.. code:: python

    apt.dist_upgrade(
        name="Upgrade apt packages using dist-upgrade",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:apt.key:

:code:`apt.key`
~~~~~~~~~~~~~~~

Add or remove APT GPG keys using modern keyring management (no ``apt-key``).

.. code:: python

    apt.key(
         src: 'str | None' = None,
         keyserver: 'str | None' = None,
         keyid: 'str | list[str] | None' = None,
         dest: 'str | None' = None,
         present: 'bool' = True,
         **kwargs,
    )

Keys are written to ``/etc/apt/keyrings/`` and can be referenced in source entries
via ``signed-by=``. The destination filename is derived automatically from the source
URL or key IDs when not specified explicitly.

+ **src**: filename or URL to a key (``.asc`` ASCII-armored or binary ``.gpg``)
+ **keyserver**: keyserver URL for fetching keys by ID
+ **keyid**: key ID or list of key IDs (required with ``keyserver``, optional for removal)
+ **dest**: destination filename or absolute path — ``.gpg`` extension is enforced;
  relative names are resolved under ``/etc/apt/keyrings/``
+ **present**: whether the key should be present (default: ``True``) or removed

.. note::
    ASCII-armored keys (``.asc``) are automatically dearmored on installation.
    Keyserver fetches use a temporary ``GNUPGHOME`` and export binary keyrings.
    Removal without ``keyid`` deletes the whole keyring file; with ``keyid`` it
    removes individual keys and prunes empty files.

.. warning::
    ``apt-key`` is deprecated in Debian. This operation follows the modern approach:
    https://wiki.debian.org/DebianRepository/UseThirdParty

**Examples:**

.. code:: python

    from pyinfra.operations import apt
    # Note: If using URL, wget is assumed to be installed.

    apt.key(
        name="Add Docker apt GPG key",
        src="https://download.docker.com/linux/debian/gpg",
        dest="docker.gpg",
    )

    apt.key(
        name="Remove specific keyring file",
        dest="old-vendor.gpg",
        present=False,
    )

    apt.key(
        name="Remove key by ID from all APT keyrings",
        keyid="0xCOMPROMISED123",
        present=False,
    )

    apt.key(
        name="Fetch keys from keyserver",
        keyserver="hkps://keyserver.ubuntu.com",
        keyid=["0xD88E42B4", "0x7EA0A9C3"],
        dest="vendor-archive.gpg",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:apt.packages:

:code:`apt.packages`
~~~~~~~~~~~~~~~~~~~~

Install/remove/update packages & update apt.

.. code:: python

    apt.packages(
         packages: 'str | list[str] | None' = None,
         present=True,
         latest=False,
         update=False,
         cache_time: 'int | None' = None,
         upgrade=False,
         force=False,
         no_recommends=False,
         allow_downgrades=False,
         purge=False,
         extra_install_args: 'str | None' = None,
         extra_uninstall_args: 'str | None' = None,
         **kwargs,
    )

+ **packages**: list of packages to ensure
+ **present**: whether the packages should be installed
+ **latest**: whether to upgrade packages without a specified version
+ **update**: run ``apt update`` before installing packages
+ **cache_time**: when used with ``update``, cache for this many seconds
+ **upgrade**: run ``apt upgrade`` before installing packages
+ **force**: whether to force package installs by passing `--force-yes` to apt
+ **no_recommends**: don't install recommended packages
+ **allow_downgrades**: allow downgrading packages with version (--allow-downgrades)
+ **purge**: when removing packages (``present=False``) use ``apt purge`` so configuration files
  are removed alongside the package
+ **extra_install_args**: additional arguments to the apt install command
+ **extra_uninstall_args**: additional arguments to the apt uninstall command

Versions:
    Package versions can be pinned like apt: ``<pkg>=<version>``

Cache time:
    When ``cache_time`` is set the ``/var/lib/apt/periodic/update-success-stamp`` file
    is touched upon successful update. Some distros already do this (Ubuntu), but others
    simply leave the periodic directory empty (Debian).

**Examples:**

.. code:: python

    # Update package list and install packages
    apt.packages(
        name="Install Asterisk and Vim",
        packages=["asterisk", "vim"],
        update=True,
    )

    # Install the latest versions of packages (always check)
    apt.packages(
        name="Install latest Vim",
        packages=["vim"],
        latest=True,
    )

    # Note: host.get_fact(OsVersion) is the same as `uname -r` (ex: '4.15.0-72-generic')
    apt.packages(
        name="Install kernel headers",
        packages=[f"linux-headers-{host.get_fact(OsVersion)}"],
        update=True,
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:apt.ppa:

:code:`apt.ppa`
~~~~~~~~~~~~~~~

.. admonition:: Stateless operation
    :class: important

    This operation will always execute commands and is not idempotent.


Add/remove Ubuntu ppa repositories.

.. code:: python

    apt.ppa(src: 'str', present=True,
         **kwargs,
    )

+ **src**: the PPA name (full ppa:user/repo format)
+ **present**: whether it should exist

Note:
    requires ``apt-add-repository`` on the remote host

**Example:**

.. code:: python

    # Note: Assumes software-properties-common is installed.
    apt.ppa(
        name="Add the Bitcoin ppa",
        src="ppa:bitcoin/bitcoin",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:apt.repo:

:code:`apt.repo`
~~~~~~~~~~~~~~~~

Add/remove apt repositories.

.. code:: python

    apt.repo(src: 'str', present=True, filename: 'str | None' = None,
         **kwargs,
    )

+ **src**: apt source string eg ``deb http://X hardy main``
+ **present**: whether the repo should exist on the system
+ **filename**: optional filename to use ``/etc/apt/sources.list.d/<filename>.list``. By
  default uses ``/etc/apt/sources.list``.

**Example:**

.. code:: python

    apt.repo(
        name="Install VirtualBox repo",
        src="deb https://download.virtualbox.org/virtualbox/debian bionic contrib",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:apt.sources_file:

:code:`apt.sources_file`
~~~~~~~~~~~~~~~~~~~~~~~~

Manage a deb822 ``.sources`` file under ``/etc/apt/sources.list.d/``.

.. code:: python

    apt.sources_file(
         filename: 'str',
         types: 'list[str] | str' = 'deb',
         uris: 'list[str] | str | None' = None,
         suites: 'list[str] | str | None' = None,
         components: 'list[str] | str | None' = None,
         architectures: 'list[str] | str | None' = None,
         signed_by: 'str | None' = None,
         present: 'bool' = True,
         **kwargs,
    )

Creates or removes a modern deb822-format sources file.  Each field that
accepts multiple values can be given as a list or a space-separated string.

+ **filename**: base name for the file (without extension); the ``.sources``
  extension is added automatically
+ **types**: repository type(s) — ``"deb"``, ``"deb-src"``, or both
+ **uris**: one or more repository URLs
+ **suites**: one or more suite/distribution names (e.g. ``"bookworm"``)
+ **components**: one or more components (e.g. ``["main", "contrib"]``)
+ **architectures**: restrict to specific architectures (e.g. ``"amd64"``)
+ **signed_by**: absolute path to the keyring file used for signature verification
+ **present**: whether the sources file should exist

**Example:**

.. code:: python

    from pyinfra.operations import apt

    apt.key(
        name="Add Docker GPG key",
        src="https://download.docker.com/linux/debian/gpg",
        dest="docker.gpg",
    )

    apt.sources_file(
        name="Add Docker apt repository (deb822)",
        filename="docker",
        types=["deb"],
        uris=["https://download.docker.com/linux/debian"],
        suites=["bookworm"],
        components=["stable"],
        architectures=["amd64"],
        signed_by="/etc/apt/keyrings/docker.gpg",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:apt.update:

:code:`apt.update`
~~~~~~~~~~~~~~~~~~

.. admonition:: Stateless operation
    :class: important

    This operation will always execute commands unless the ``cache_time`` argument is provided.


Updates apt repositories.

.. code:: python

    apt.update(cache_time: 'int | None' = None,
         **kwargs,
    )

+ **cache_time**: cache updates for this many seconds

**Example:**

.. code:: python

    apt.update(
        name="Update apt repositories",
        cache_time=3600,
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:apt.upgrade:

:code:`apt.upgrade`
~~~~~~~~~~~~~~~~~~~

Upgrades all apt packages.

.. code:: python

    apt.upgrade(auto_remove: 'bool' = False,
         **kwargs,
    )

+ **auto_remove**: removes transitive dependencies that are no longer needed.

**Example:**

.. code:: python

    # Upgrade all packages
    apt.upgrade(
        name="Upgrade apt packages",
    )

    # Upgrade all packages and remove unneeded transitive dependencies
    apt.upgrade(
        name="Upgrade apt packages and remove unneeded dependencies",
        auto_remove=True
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.

