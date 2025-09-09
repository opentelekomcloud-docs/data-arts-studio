:original_name: dataartsstudio_01_0576.html

.. _dataartsstudio_01_0576:

Creating a CDM Cluster
======================

CDM provides independent clusters for secure and reliable data migration. Clusters are isolated from each other and cannot access each other.

CDM clusters can be used in the following scenarios:

-  They can be used to create and run data migration jobs.
-  They can function as agents for connecting Management Center to a data lake.

Prerequisites
-------------

You have applied for a VPC, subnet, and security group. If the CDM cluster tries to connect to another cloud service, ensure that the cluster and the cloud service are in the same VPC. Otherwise, an EIP is required.

.. note::

   -  If the CDM cluster and a cloud service are in the same region, VPC, subnet, and security group, they can communicate with each other through an intranet.

   -  If the CDM cluster and the cloud service are in the same region and VPC but in different subnets or security groups, you must configure routing rules and security group rules. For details about how to configure routing rules, see "Adding Routes to a Route Table" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*. For details about how to configure security group rules, see "Security Group" > "Adding a Security Group Rule" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*.

   -  If the CDM cluster and a cloud service are in different VPCs of the same region, you can create a VPC peering connection to enable them to communicate with each other. For details about how to configure a VPC peering connection, see "VPC Peering Connection" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*

      Note: If a VPC peering connection is created, the peer VPC subnet may overlap with the CDM management network. As a result, data sources in the peer VPC cannot be accessed. You are advised to use the Internet for cross-VPC data migration, or contact the administrator to add specific routes for the VPC peering connection in the CDM background.

   -  If the CDM cluster and a cloud service are located in different regions, you need to use the Internet or Direct Connect to enable them to communicate with each other. When using the Internet, ensure that an EIP has been bound to the CDM cluster, the security group of CDM allows outbound traffic from the host where the off-cloud data source is located, the host where the data source is located can access the Internet, and the connection port has been enabled in the firewall rules.

   -  In addition, an enterprise project may also affect the communication between the CDM cluster and other cloud services. The CDM cluster can communicate with a cloud service only if they have the same enterprise project.

Scenario
--------

The DataArts Studio instance does not contain CDM clusters. To use CDM, create a CDM cluster by following the instructions in :ref:`Creating a DataArts Migration Incremental Package <dataartsstudio_01_0119>`.
