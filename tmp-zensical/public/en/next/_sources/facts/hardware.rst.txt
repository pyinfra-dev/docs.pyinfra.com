Hardware Facts
--------------

.. _facts:hardware.BlockDevices:

:code:`hardware.BlockDevices`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(BlockDevices)

Returns a dict of (mounted) block devices:

.. code:: python

    {
        "/dev/sda1": {
            "available": "39489508",
            "used_percent": "3",
            "mount": "/",
            "used": "836392",
            "blocks": "40325900"
        },
    }


.. _facts:hardware.CpuInfo:

:code:`hardware.CpuInfo`
~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(CpuInfo)

Returns dict of information returned by lscpu command.

.. code:: python

    {
        "Architecture": "x86_64",
        "CPU op-mode(s)": "32-bit, 64-bit",
        "Address sizes": "36 bits physical, 48 bits virtual",
        "Byte Order": "Little Endian",
        "CPU(s)": "4",
        "On-line CPU(s) list": "0-3",
        "Vendor ID": "GenuineIntel",
        "Model name": "Intel(R) Atom(TM) CPU N2800   @ 1.86GHz",
        "CPU family": "6",
        "Model": "54",
        "Thread(s) per core": "2",
        "Core(s) per socket": "2",
        "Socket(s)": "1",
        "Stepping": "1",
        "CPU(s) scaling MHz": "48%",
        "CPU max MHz": "1862,0000",
        "CPU min MHz": "798,0000",
        "BogoMIPS": "3735,20",
        "Flags": [
            "fpu",
            "vme",
            "de",
            "pse",
            "tsc",
            "msr",
            "pae",
            "mce",
            "cx8",
            "apic",
            "sep",
            "mtrr",
            "pge",
            "mca",
            "cmov",
            "pat",
            "pse36",
            "clflush",
            "dts",
            "acpi",
            "mmx",
            "fxsr",
            "sse",
            "sse2",
            "ss",
            "ht",
            "tm",
            "pbe",
            "syscall",
            "nx",
            "lm",
            "constant_tsc",
            "arch_perfmon",
            "pebs",
            "bts",
            "nopl",
            "nonstop_tsc",
            "cpuid",
            "aperfmperf",
            "pni",
            "dtes64",
            "monitor",
            "ds_cpl",
            "est",
            "tm2",
            "ssse3",
            "cx16",
            "xt",
            "pr",
            "pdcm",
            "movbe",
            "lahf_lm",
            "dtherm",
            "arat"
        ],
        "L1d cache": "48 KiB (2 instances)",
        "L1i cache": "64 KiB (2 instances)",
        "L2 cache": "1 MiB (2 instances)",
        "NUMA node(s)": "1",
        "NUMA node0 CPU(s)": "0-3",
        "Vulnerability Itlb multihit": "Not affected",
        "Vulnerability L1tf": "Not affected",
        "Vulnerability Mds": "Not affected",
        "Vulnerability Meltdown": "Not affected",
        "Vulnerability Spec store bypass": "Not affected",
        "Vulnerability Spectre v1": "Not affected",
        "Vulnerability Spectre v2": "Not affected",
        "Vulnerability Srbds": "Not affected",
        "Vulnerability Tsx async abort": "Not affected"
    }


.. _facts:hardware.Cpus:

:code:`hardware.Cpus`
~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(Cpus)

Returns the number of CPUs on this server.


.. _facts:hardware.Ipv4Addresses:

:code:`hardware.Ipv4Addresses`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(Ipv4Addresses)

Gets & returns a dictionary of network interface -> IPv4 address.

.. code:: python

    {
        "eth0": "127.0.0.1",
    }

.. warning::
    This fact is deprecated, please use the ``hardware.Ipv4Addrs`` fact.

.. note::
    Network interfaces with no IPv4 will not be part of the dictionary.


.. _facts:hardware.Ipv4Addrs:

:code:`hardware.Ipv4Addrs`
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(Ipv4Addrs)

Gets & returns a dictionary of network interface -> list of IPv4 addresses.

.. code:: python

    {
        "eth0": ["127.0.0.1"],
    }

.. note::
    Network interfaces with no IPv4 will not be part of the dictionary.


.. _facts:hardware.Ipv6Addresses:

:code:`hardware.Ipv6Addresses`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(Ipv6Addresses)

Gets & returns a dictionary of network interface -> IPv6 address.

.. code:: python

    {
        "eth0": "fe80::a00:27ff::2",
    }

.. warning::
    This fact is deprecated, please use the ``hardware.Ipv6Addrs`` fact.

.. note::
    Network interfaces with no IPv6 will not be part of the dictionary.


.. _facts:hardware.Ipv6Addrs:

:code:`hardware.Ipv6Addrs`
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(Ipv6Addrs)

Gets & returns a dictionary of network interface -> list of IPv6 addresses.

.. code:: python

    {
        "eth0": ["fe80::a00:27ff::2"],
    }

.. note::
    Network interfaces with no IPv6 will not be part of the dictionary.


.. _facts:hardware.Memory:

:code:`hardware.Memory`
~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(Memory)

Returns the memory installed in this server, in MB.


.. _facts:hardware.NetworkDevices:

:code:`hardware.NetworkDevices`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    host.get_fact(NetworkDevices)

Gets & returns a dict of network devices. See the ``ipv4_addresses`` and
``ipv6_addresses`` facts for easier-to-use shortcuts to get device addresses.

.. code:: python

    "enp1s0": {
        "ether": "12:34:56:78:9A:BC",
        "mtu": 1500,
        "state": "UP",
        "ipv4": {
            "address": "192.168.1.100",
            "mask_bits": 24,
            "netmask": "255.255.255.0"
        },
        "ipv6": {
            "address": "2001:db8:85a3::8a2e:370:7334",
            "mask_bits": 64,
            "additional_ips": [
                {
                    "address": "fe80::1234:5678:9abc:def0",
                    "mask_bits": 64
                }
            ]
        }
    },
    "incusbr0": {
        "ether": "DE:AD:BE:EF:CA:FE",
        "mtu": 1500,
        "state": "UP",
        "ipv4": {
            "address": "10.0.0.1",
            "mask_bits": 24,
            "netmask": "255.255.255.0"
        },
        "ipv6": {
            "address": "fe80::dead:beef:cafe:babe",
            "mask_bits": 64,
            "additional_ips": [
                {
                    "address": "2001:db8:1234:5678::1",
                    "mask_bits": 64
                }
            ]
        }
    },
    "lo": {
        "mtu": 65536,
        "state": "UP",
        "ipv6": {
            "address": "::1",
            "mask_bits": 128
        }
    },
    "veth98806fd6": {
        "ether": "AA:BB:CC:DD:EE:FF",
        "mtu": 1500,
        "state": "UP"
    },
    "vethda29df81": {
        "ether": "11:22:33:44:55:66",
        "mtu": 1500,
        "state": "UP"
    },
    "wlo1": {
        "ether": "77:88:99:AA:BB:CC",
        "mtu": 1500,
        "state": "UNKNOWN"
    }

