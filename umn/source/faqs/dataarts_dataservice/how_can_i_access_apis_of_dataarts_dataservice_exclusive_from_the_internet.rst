:original_name: dataartsstudio_03_0239.html

.. _dataartsstudio_03_0239:

How Can I Access APIs of DataArts DataService Exclusive from the Internet?
==========================================================================

The APIs can be accessed from the Internet only if the DataArts DataService Exclusive cluster can be accessed from the Internet.

To enable access to the DataArts DataService Exclusive cluster from the Internet, select **Enable public Access** when creating the cluster. After a DataArts DataService Exclusive cluster is created, you cannot bind an EIP to it if **Enable public Access** was not selected during the cluster creation, that is, the cluster cannot be accessed from the Internet.

In this case, you can export APIs of the current cluster, create another DataArts DataService Exclusive cluster and select **Enable public Access**, and import APIs from the old cluster to the new cluster to enable public network access.
