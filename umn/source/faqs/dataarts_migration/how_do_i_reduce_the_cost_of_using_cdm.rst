:original_name: dataartsstudio_03_0099.html

.. _dataartsstudio_03_0099:

How Do I Reduce the Cost of Using CDM?
======================================

When migrating the data on the public network, use NAT Gateway to share the EIPs with other ECSs in the subnet. In this way, data on the on-premises data center or third-party cloud can be migrated in a more economical and convenient manner.

The following details the operations:

#. Suppose that you have created a CDM cluster (no dedicated EIP needs to be bound to the CDM cluster). Record the VPC and subnet where the CDM cluster is located.

#. Create a NAT gateway. Select the same VPC and subnet as the CDM cluster.

#. After the NAT gateway is created, return to the NAT gateway console list, click the created gateway name, and then click **Add SNAT Rule**.

#. Select a subnet and an EIP. If no EIP is available, apply for one.

   After that, access the CDM management console and migrate data from the public network to the cloud through the Internet. For example, migrate files from the FTP server in the on-premises data center to OBS and migrate relational databases from the third-party cloud to RDS.
