Git Facts
---------

See also: :doc:`../operations/git`.

.. _facts:git.GitBranch:

:code:`git.GitBranch`
~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GitBranch, repo)


.. _facts:git.GitConfig:

:code:`git.GitConfig`
~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GitConfig, repo=None, system=False)


.. _facts:git.GitLocalCommit:

:code:`git.GitLocalCommit`
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GitLocalCommit, repo, ref='HEAD')

Returns the SHA of ``ref`` (defaults to ``HEAD``) in a local git repository,
or ``None`` when the repository does not exist, the ref is unknown, or the
command fails.


.. _facts:git.GitRemoteBranchCommit:

:code:`git.GitRemoteBranchCommit`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GitRemoteBranchCommit, repo, remote='origin', branch=None)

Returns the SHA of the tip of ``branch`` on ``remote`` as reported by
``git ls-remote``. Returns ``None`` when the remote is unreachable, the
branch does not exist on the remote, or the repository is missing.


.. _facts:git.GitTag:

:code:`git.GitTag`
~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GitTag, repo)


.. _facts:git.GitTrackingBranch:

:code:`git.GitTrackingBranch`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(GitTrackingBranch, repo)

