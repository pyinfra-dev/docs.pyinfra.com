``@ssh`` Connector
------------------

Connect to hosts over SSH. This is the default connector and all targets default
to this meaning you do not need to specify it - ie the following two commands
are identical:

.. code:: shell

    pyinfra my-host.net ...
    pyinfra @ssh/my-host.net ...

Examples
~~~~~~~~

An inventory file (``inventory.py``) containing a single SSH target with SSH
forward agent enabled:

.. code:: python

    hosts = [
        ("my-host.net", {"ssh_forward_agent": True}),
    ]

Multiple hosts sharing the same SSH username:

.. code:: python

    hosts = (
        ["my-host-1.net", "my-host-2.net"],
        {"ssh_user": "ssh-user"},
    )

Multiple hosts with different SSH usernames:

.. code:: python

    hosts = [
        ("my-host-1.net", {"ssh_user": "ssh-user"}),
        ("my-host-2.net", {"ssh_user": "other-user"}),
    ]

Available Data
~~~~~~~~~~~~~~

The following keys can be set as host or group data to control how this connector interacts with the target.

.. list-table::
   :header-rows: 1
   :widths: 25 45 15 15

   * - Key
     - Description
     - Type
     - Default
   * - ``ssh_hostname``
     - SSH hostname
     - ``str``
     - 

   * - ``ssh_port``
     - SSH port
     - ``int``
     - 

   * - ``ssh_user``
     - SSH user
     - ``str``
     - 

   * - ``ssh_password``
     - SSH password
     - ``str``
     - 

   * - ``ssh_key``
     - SSH key filename
     - ``str``
     - 

   * - ``ssh_key_password``
     - SSH key password
     - ``str``
     - 

   * - ``ssh_allow_agent``
     - Whether to use any active SSH agent
     - ``bool``
     - ``True``

   * - ``ssh_look_for_keys``
     - Whether to look for private keys
     - ``bool``
     - ``True``

   * - ``ssh_forward_agent``
     - Whether to enable SSH forward agent
     - ``bool``
     - ``False``

   * - ``ssh_config_file``
     - SSH config filename
     - ``str``
     - 

   * - ``ssh_known_hosts_file``
     - SSH known_hosts filename
     - ``str``
     - 

   * - ``ssh_strict_host_key_checking``
     - SSH strict host key checking
     - ``str``
     - ``accept-new``

   * - ``ssh_paramiko_connect_kwargs``
     - Override keyword arguments passed into Paramiko's ``SSHClient.connect``
     - ``dict``
     - 

   * - ``ssh_connect_retries``
     - Number of tries to connect via ssh
     - ``int``
     - ``0``

   * - ``ssh_connect_retry_min_delay``
     - Lower bound for random delay between retries
     - ``float``
     - ``0.1``

   * - ``ssh_connect_retry_max_delay``
     - Upper bound for random delay between retries
     - ``float``
     - ``0.5``

   * - ``ssh_file_transfer_protocol``
     - Protocol to use for file transfers. Can be ``sftp`` or ``scp``.
     - ``str``
     - ``sftp``
