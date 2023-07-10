:original_name: dataartsstudio_03_0119.html

.. _dataartsstudio_03_0119:

How Do I Configure the Connection If Only Some Nodes in the HANA Cluster Can Communicate with the CDM Cluster?
==============================================================================================================

To ensure that CDM can communicate with the HANA cluster, perform the following operations:

#. Disable Statement Routing of the HANA cluster. Note that this will increase the pressure on configuration nodes.
#. When creating a HANA link, add the advanced attribute **distribution** and set its value to **off**.

After the preceding configurations are complete, CDM can communicate with the HANA cluster.
