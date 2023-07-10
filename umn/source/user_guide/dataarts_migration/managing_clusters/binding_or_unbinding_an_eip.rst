:original_name: dataartsstudio_01_0020.html

.. _dataartsstudio_01_0020:

Binding or Unbinding an EIP
===========================

Scenario
--------

After creating a CDM cluster, you can bind an EIP to or unbind an EIP from the cluster.

-  If CDM needs to access a local or Internet data source, or a cloud service in another VPC, bind an EIP to the CDM cluster or use a NAT gateway to enable the CDM cluster to share the EIP with ECSs to access the Internet..
-  To create an EIP exception notification, choose **Authorize EIP Check** > **Create Agency** on the **Cluster Management** page. The EIP exception notification takes effect only after the VPC policy agency of the corresponding region is created on the IAM management console.

.. note::

   If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

Prerequisites
-------------

-  You have created a CDM cluster.
-  Your EIP quota is sufficient.

Procedure
---------

#. Access the CDM console and choose **Cluster Management** in the left navigation pane.


   .. figure:: /_static/images/en-us_image_0000001322088024.png
      :alt: **Figure 1** Cluster list

      **Figure 1** Cluster list

   .. note::

      The **Source** column is displayed only when you access the **DataArts Migration** page from the DataArts Studio console.

#. Bind an EIP to or unbind an EIP from a cluster.

   -  Binding an EIP: In the **Operation** column, click **Bind EIP**. The **Bind EIP** dialog box is displayed.
   -  Unbinding an EIP: In the **Operation** column, choose **More** > **Unbind EIP**.

#. Click **Yes**.
