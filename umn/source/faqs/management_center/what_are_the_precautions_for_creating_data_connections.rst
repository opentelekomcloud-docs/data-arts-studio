:original_name: dataartsstudio_03_0009.html

.. _dataartsstudio_03_0009:

What Are the Precautions for Creating Data Connections?
=======================================================

-  RDS data connections depend on OBS. If OBS is unavailable in the same region as DataArts Studio, RDS data connections are not supported.

-  For host connections, only Linux hosts are supported.

-  If changes occur in the connected data lake (for example, the MRS cluster capacity is expanded), you need to edit and save the connection.

-  If the data lake authentication information in a data connection changes (for example, the password expires), the data connection becomes invalid. Ensure that the data lake authentication information is permanently valid to prevent any loss caused by connection failures.

-  DataArts Studio does not support MRS clusters whose Kerberos encryption type is **aes256-sha2,aes128-sha2**, and only supports MRS clusters whose Kerberos encryption type is **aes256-sha1,aes128-sha1**.

-  If a CDM cluster functions as the agent for a data connection in Management Center, the cluster supports a maximum of 200 concurrent active threads. If multiple data connections share an agent, a maximum of 200 SQL, Shell, and Python scripts submitted through the connections can run concurrently. Excess tasks will be queued. You are advised to plan multiple agents based on the workload.

-  Before creating a data connection, ensure that you have obtained the required agent (CDM cluster) and that the CDM cluster can communicate with the data lake to be connected.

   -  If the data lake is an on-premises database, you need the Internet or Direct Connect. Ensure that the host where the data source is located and the CDM cluster can access the Internet, and the connection port has been enabled in the firewall rule.
   -  If the data lake is a cloud service (such as DWS and MRS), the following requirements must be met for network interconnection:

      -  If the CDM cluster and the cloud service are in different regions, a public network or a dedicated connection is required for enabling communication between the CDM cluster and the cloud service.
      -  If the CDM cluster and the cloud service are in the same region, VPC, subnet, and security group, they can communicate with each other by default. If they are in the same VPC but in different subnets or security groups, you must configure routing rules and security group rules. For details about how to configure routing rules, see "Adding Routes to a Route Table" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*. For details about how to configure security group rules, see "Security Group" > "Adding a Security Group Rule" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*.
      -  The cloud service instance and the DataArts Studio workspace belong to the same enterprise project. If they do not, you can modify the enterprise project of the workspace.
