Gpg Operations
--------------


Manage GPG keys and keyrings.


Facts used in these operations: :ref:`facts:gpg.GpgKeyrings`.

.. _operations:gpg.dearmor:

:code:`gpg.dearmor`
~~~~~~~~~~~~~~~~~~~

Convert ASCII armored GPG key to binary format.

.. code:: python

    gpg.dearmor(src: str, dest: str, mode: str = '0644',
         **kwargs,
    )

+ **src**: source ASCII armored key file
+ **dest**: destination binary key file
+ **mode**: file permissions for the output file

**Example:**

.. code:: python

    gpg.dearmor(
        name="Convert key to binary",
        src="/tmp/key.asc",
        dest="/etc/apt/keyrings/key.gpg",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.


.. _operations:gpg.key:

:code:`gpg.key`
~~~~~~~~~~~~~~~

Install or remove GPG keys from various sources.

.. code:: python

    gpg.key(
         src: str | None = None,
         dest: str | None = None,
         keyserver: str | None = None,
         keyid: str | list[str] | None = None,
         dearmor: bool = True,
         mode: str = '0644',
         present: bool = True,
         working_dirs: list[str] | None = None,
         **kwargs,
    )

+ **src**: filename or URL to a key (ASCII .asc or binary .gpg)
+ **dest**: destination path for the key file (required for installation, optional for removal)
+ **keyserver**: keyserver URL for fetching keys by ID
+ **keyid**: key ID or list of key IDs (required with keyserver, optional for removal)
+ **dearmor**: whether to convert ASCII armored keys to binary format
+ **mode**: file permissions for the installed key
+ **present**: whether the key should be present (True) or absent (False)
+ **working_dirs**: dirs to search for existing keyrings (required for removal without dest).
  When False: if dest is provided, removes from specific keyring;
  if dest is None, removes from keyrings found in working_dirs;
  if keyid is provided, removes specific key(s);
  if keyid is None, removes entire keyring file(s)

**Examples:**

.. code:: python

    gpg.key(
        name="Install Docker GPG key",
        src="https://download.docker.com/linux/debian/gpg",
        dest="/etc/apt/keyrings/docker.gpg",
    )

    gpg.key(
        name="Remove old GPG key file",
        dest="/etc/apt/keyrings/old-key.gpg",
        present=False,
    )

    gpg.key(
        name="Remove specific key by ID",
        dest="/etc/apt/keyrings/vendor.gpg",
        keyid="0xABCDEF12",
        present=False,
    )

    gpg.key(
        name="Remove key from specific directories",
        keyid="0xCOMPROMISED123",
        present=False,
        working_dirs=["/etc/apt/keyrings", "/usr/share/keyrings"],
    )

    gpg.key(
        name="Fetch keys from keyserver",
        keyserver="hkps://keyserver.ubuntu.com",
        keyid=["0xD88E42B4", "0x7EA0A9C3"],
        dest="/etc/apt/keyrings/vendor.gpg",
    )

.. note::
    This operation also inherits all :doc:`global arguments </arguments>`.

