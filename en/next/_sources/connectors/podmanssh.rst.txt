``@podmanssh`` Connector
------------------------

**Note**: this connector is in beta!

The ``@podmanssh`` connector allows you to run commands on Podman containers
on a remote machine over SSH. This is useful when you need to manage containers
running on remote hosts where Podman is installed instead of Docker.

.. note::

    This connector requires SSH access to the remote host and Podman to be installed
    on the target machine. It operates similarly to ``@dockerssh`` but uses the
    ``podman`` command instead of ``docker``.

+ **Remote container creation**: Creates a new container from the specified image on the remote host
+ **Command execution**: Runs operations inside the container via ``podman exec``
+ **File operations**: Supports uploading/downloading files to/from containers via ``podman cp``
+ **Container cleanup**: Automatically commits and removes containers when operations complete

.. code:: shell

    # A Podman base image must be provided
    pyinfra @podmanssh/remotehost:alpine:3.8 ...

    # Run operations on multiple remote Podman containers in parallel
    pyinfra @podmanssh/web1:nginx:latest,@podmanssh/web2:nginx:latest deploy.py

    # Use with specific SSH connection settings
    pyinfra @podmanssh/production-server:alpine:3.18 --sudo --port 2222 operations/

**Comparison with other connectors:**

+ Use ``@podman`` for local Podman containers
+ Use ``@dockerssh`` for remote Docker containers
+ Use ``@podmanssh`` for remote Podman containers (this connector)

The Podman SSH connector is particularly useful in environments where:

+ Docker is not available but Podman is installed
+ Rootless containers are preferred for security
+ You need OCI-compliant container operations on remote hosts

Usage
~~~~~

.. code:: shell

        pyinfra @podmanssh/name ...
