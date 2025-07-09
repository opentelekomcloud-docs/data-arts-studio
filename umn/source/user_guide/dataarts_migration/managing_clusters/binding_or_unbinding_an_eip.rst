:original_name: dataartsstudio_01_0020_0.html

.. _dataartsstudio_01_0020_0:

Binding or Unbinding an EIP
===========================

Scenario
--------

After creating a CDM cluster, you can bind an EIP to or unbind an EIP from the cluster.

If CDM needs to access a local or Internet data source, or a cloud service in another VPC, bind an EIP to the CDM cluster or use a NAT gateway to enable the CDM cluster to share the EIP with ECSs to access the Internet.

.. note::

   If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

Prerequisites
-------------

-  You have created a CDM cluster.
-  Your EIP quota is sufficient.

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`. On the DataArts Studio console, locate a workspace and click **DataArts Migration** to access the CDM console.
#. Bind an EIP to or unbind an EIP from a cluster.

   -  Binding an EIP: In the **Operation** column, click **Bind EIP**. The **Bind EIP** dialog box is displayed.
   -  Unbinding an EIP: In the **Operation** column, choose **More** > **Unbind EIP**.

#. Click **Yes**.
