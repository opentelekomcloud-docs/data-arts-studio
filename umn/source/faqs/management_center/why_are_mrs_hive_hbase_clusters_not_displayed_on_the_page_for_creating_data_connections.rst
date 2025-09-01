:original_name: dataartsstudio_03_0017.html

.. _dataartsstudio_03_0017:

Why Are MRS Hive/HBase Clusters Not Displayed on the Page for Creating Data Connections?
========================================================================================

Possible causes are as follows:

-  Hive/HBase components were not selected during MRS cluster creation.

-  The enterprise project selected during MRS cluster creation is different from that in the workspace.

-  The network between the CDM cluster and MRS cluster was disconnected when an MRS data connection is created.

   The CDM cluster functions as a network agent. MRS data connections that you are going to create need to communicate with CDM.
