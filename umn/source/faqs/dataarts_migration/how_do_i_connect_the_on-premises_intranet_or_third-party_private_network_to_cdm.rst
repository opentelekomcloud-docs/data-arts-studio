:original_name: dataartsstudio_03_0033.html

.. _dataartsstudio_03_0033:

How Do I Connect the On-Premises Intranet or Third-Party Private Network to CDM?
================================================================================

Many enterprises deploy key data sources on the intranet, such as databases and file servers. CDM runs on the cloud. To migrate the intranet data to the cloud using CDM, use any of the following methods to connect the intranet to the cloud:

-  If the destination data source is an on-premises database, you need the Internet or Direct Connect. When using the Internet, ensure that an EIP has been bound to the CDM cluster, the security group of CDM allows outbound traffic from the host where the off-cloud data source is located, the host where the data source is located can access the Internet, and the connection port has been enabled in the firewall rules.
-  Establish a VPN between the on-premises data center and the VPC where the service resides.
-  Leverage Network Address Translation (NAT) or port forwarding to access the network in proxy mode.

The following describes how to use the port forwarding tool to access intranet data. The process is as follows:

#. Use a Windows computer as the gateway. The computer must be able to access both the Internet and the intranet.
#. Install the port mapping tool IPOP on the computer.
#. Configure port mapping using the tool.

.. important::

   If the intranet database is exposed to the public network for a long time, security risks exist. Therefore, after data migration is complete, stop port mapping.

Scenario
--------

Suppose that the MySQL database on the intranet is migrated to DWS.

In the figure, the intranet can be either an enterprise's data center or the intranet of the virtual data center on a third-party cloud.


.. figure:: /_static/images/en-us_image_0000002305438701.png
   :alt: **Figure 1** Network topology example

   **Figure 1** Network topology example

Procedure
---------

#. Use a Windows computer as the gateway. Configure both the intranet and Internet IP addresses on the computer. Conduct the following test to check whether the gateway computer can fulfill service needs.

   a. Run the **ping** command on the computer to check whether the intranet address of the MySQL database is pingable. For example, run **ping 192.168.1.8**.
   b. Run the **ping** command on another computer that can access the Internet to check whether the public network address of the gateway computer is pingable. For example, run **ping 202.**\ *xx*\ **.**\ *xx*\ **.10**.

#. Download the port mapping tool IPOP and install it on the gateway computer.

#. Run the port mapping tool and select **PORT Map**. See :ref:`Figure 2 <dataartsstudio_03_0033__en-us_topic_0108275483_fig30424171101712>`.

   -  **Local IP** and **Local Port**: Configure these two parameters to the public network address and port number of the gateway computer respectively, which must be entered when creating MySQL links on CDM.
   -  **Mapping IP** and **Map Port**: Configure these two parameters to the IP address and port number of the MySQL database on the intranet.

   .. _dataartsstudio_03_0033__en-us_topic_0108275483_fig30424171101712:

   .. figure:: /_static/images/en-us_image_0000002305438709.png
      :alt: **Figure 2** Configuring port mapping

      **Figure 2** Configuring port mapping

#. Click **ADD** to add a port mapping relationship.

#. Click **START** to start mapping and receive data packets.

   Then, you can use the EIP to read data from the MySQL database on the intranet on CDM and import the data to DWS.

   .. note::

      a. To access the on-premises data source, you must also bind an EIP to the CDM cluster.
      b. Generally, DWS is accessible within the same VPC. When creating a CDM cluster, you must ensure that the VPC of the CDM cluster must be the same as that of DWS. In addition, it is recommended that CDM and DWS be in the same intranet and security group. If their security groups are different, you also need to enable data access between the security groups.
      c. Port mapping can be used to migrate data between databases on the intranet or the SFTP servers.
      d. For Linux computers, port mapping can also be implemented using IPTABLE.
      e. When the FTP server on the intranet is mapped to the public network using port mapping, you need to check whether the PASV mode is enabled. In this case, the client and server are connected through a random port. Therefore, in addition to port 21 mapping, you also need to configure the port range mapping in PASV mode. For example, you can specify the **vsftp** port range by configuring **pasv_min_port** and **pasv_max_port**.
