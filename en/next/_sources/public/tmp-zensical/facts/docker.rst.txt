Docker Facts
------------


Facts about Docker containers, volumes and networks. These facts give you information from the view
of the current inventory host. See the :doc:`../connectors/docker` to use Docker containers as
inventory directly.

See also: :doc:`../operations/docker`.

.. _facts:docker.DockerAuths:

:code:`docker.DockerAuths`
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerAuths)

Returns the list of registry servers the current user is authenticated
against, read from ``${DOCKER_CONFIG:-$HOME/.docker}/config.json``.

Returns an empty list if no config file exists or no auths are stored.


.. _facts:docker.DockerContainer:

:code:`docker.DockerContainer`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainer, object_id)

Returns ``docker inspect`` output for a single Docker container.


.. _facts:docker.DockerContainerEnvs:

:code:`docker.DockerContainerEnvs`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainerEnvs)

Returns environment variables for all Docker containers, keyed by container ID.


.. _facts:docker.DockerContainerFsChanges:

:code:`docker.DockerContainerFsChanges`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainerFsChanges, container_id)

Returns filesystem changes for a single container (``docker diff``) as a list of
``{"path": ..., "change": "A"|"C"|"D"}`` entries.


.. _facts:docker.DockerContainerLabels:

:code:`docker.DockerContainerLabels`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainerLabels)

Returns labels for all Docker containers, keyed by container ID.


.. _facts:docker.DockerContainerMounts:

:code:`docker.DockerContainerMounts`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainerMounts)

Returns mounts for all Docker containers, keyed by container ID.


.. _facts:docker.DockerContainerNetworks:

:code:`docker.DockerContainerNetworks`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainerNetworks)

Returns networks for all Docker containers, keyed by container ID.


.. _facts:docker.DockerContainerPorts:

:code:`docker.DockerContainerPorts`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainerPorts)

Returns published port bindings for all Docker containers, keyed by container ID.


.. _facts:docker.DockerContainerProcesses:

:code:`docker.DockerContainerProcesses`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainerProcesses, container_id)

Returns processes running inside a single container (``docker top``) as a list of
column dicts. Column names follow the ``ps`` output header.


.. _facts:docker.DockerContainerStats:

:code:`docker.DockerContainerStats`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainerStats)

Returns resource-usage stats for all running containers (``docker stats``) as a list
of dicts (one entry per container).


.. _facts:docker.DockerContainers:

:code:`docker.DockerContainers`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerContainers)

Returns ``docker inspect`` output for all Docker containers.


.. _facts:docker.DockerImage:

:code:`docker.DockerImage`
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerImage, object_id)

Returns ``docker inspect`` output for a single Docker image.


.. _facts:docker.DockerImageHistory:

:code:`docker.DockerImageHistory`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerImageHistory, image_id)

Returns the layer history of a single image (``docker history``) as a list of dicts.


.. _facts:docker.DockerImageLabels:

:code:`docker.DockerImageLabels`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerImageLabels)

Returns labels for all Docker images, keyed by image ID.


.. _facts:docker.DockerImageLayers:

:code:`docker.DockerImageLayers`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerImageLayers)

Returns layer digests for all Docker images, keyed by image ID.


.. _facts:docker.DockerImages:

:code:`docker.DockerImages`
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerImages)

Returns ``docker inspect`` output for all Docker images.


.. _facts:docker.DockerNetwork:

:code:`docker.DockerNetwork`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerNetwork, object_id)

Returns ``docker inspect`` output for a single Docker network.


.. _facts:docker.DockerNetworkLabels:

:code:`docker.DockerNetworkLabels`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerNetworkLabels)

Returns labels for all Docker networks, keyed by network ID.


.. _facts:docker.DockerNetworks:

:code:`docker.DockerNetworks`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerNetworks)

Returns ``docker inspect`` output for all Docker networks.


.. _facts:docker.DockerPlugin:

:code:`docker.DockerPlugin`
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerPlugin, object_id)

Returns ``docker plugin inspect`` output for a single Docker plugin.


.. _facts:docker.DockerPlugins:

:code:`docker.DockerPlugins`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerPlugins)

Returns ``docker plugin inspect`` output for all Docker plugins.


.. _facts:docker.DockerSingleMixin:

:code:`docker.DockerSingleMixin`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerSingleMixin, object_id)


.. _facts:docker.DockerSystemInfo:

:code:`docker.DockerSystemInfo`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerSystemInfo)

Returns ``docker system info`` output in JSON format.


.. _facts:docker.DockerVersion:

:code:`docker.DockerVersion`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerVersion)

Returns the Docker version.


.. _facts:docker.DockerVolume:

:code:`docker.DockerVolume`
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerVolume, object_id)

Returns ``docker inspect`` output for a single Docker container.


.. _facts:docker.DockerVolumeLabels:

:code:`docker.DockerVolumeLabels`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerVolumeLabels)

Returns labels for all Docker volumes, keyed by volume name.


.. _facts:docker.DockerVolumes:

:code:`docker.DockerVolumes`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(DockerVolumes)

Returns ``docker inspect`` output for all Docker volumes.

