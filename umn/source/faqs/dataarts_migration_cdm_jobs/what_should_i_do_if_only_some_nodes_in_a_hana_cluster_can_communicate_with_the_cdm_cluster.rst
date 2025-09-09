:original_name: dataartsstudio_03_0119.html

.. _dataartsstudio_03_0119:

What Should I Do If Only Some Nodes in a HANA Cluster Can Communicate with the CDM Cluster?
===========================================================================================

Symptom
-------

What should I do If only some nodes in a HANA cluster can communicate with the CDM cluster?

Solution
--------

To ensure that CDM can communicate with the HANA cluster, perform the following operations:

#. Disable Statement Routing of the HANA cluster. Note that this will increase the pressure on configuration nodes.
#. When creating a HANA link, add the advanced attribute **distribution** and set its value to **off**.

After the preceding configurations are complete, CDM can communicate with the HANA cluster.
