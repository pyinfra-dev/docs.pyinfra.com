Iptables Facts
--------------

See also: :doc:`../operations/iptables`.

.. _facts:iptables.Ip6tablesChains:

:code:`iptables.Ip6tablesChains`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(Ip6tablesChains, table='filter')

Returns a dict of ip6tables chains & policies:

.. code:: python

    {
        "NAME": "POLICY",
    }


.. _facts:iptables.Ip6tablesRules:

:code:`iptables.Ip6tablesRules`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(Ip6tablesRules, table='filter')

Returns a list of ip6tables rules for a specific table:

.. code:: python

    [
        {
            "chain": "PREROUTING",
            "jump": "DNAT",
        },
    ]


.. _facts:iptables.IptablesChains:

:code:`iptables.IptablesChains`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(IptablesChains, table='filter')

Returns a dict of iptables chains & policies:

.. code:: python

    {
        "NAME": "POLICY",
    }


.. _facts:iptables.IptablesRules:

:code:`iptables.IptablesRules`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(IptablesRules, table='filter')

Returns a list of iptables rules for a specific table:

.. code:: python

    [
        {
            "chain": "PREROUTING",
            "jump": "DNAT",
        },
    ]

