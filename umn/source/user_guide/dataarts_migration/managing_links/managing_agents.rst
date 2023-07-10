:original_name: dataartsstudio_01_0128.html

.. _dataartsstudio_01_0128:

Managing Agents
===============

If your data is stored in HDFS or a relational database, you can deploy an agent on the source network. CDM pulls data from your internal data sources through an agent but cannot write data into the databases.

:ref:`Figure 1 <dataartsstudio_01_0128__en-us_topic_0207402273_en-us_topic_0191978474_fig581611212343>` shows the process of using an agent.

.. _dataartsstudio_01_0128__en-us_topic_0207402273_en-us_topic_0191978474_fig581611212343:

.. figure:: /_static/images/en-us_image_0000001373087821.jpg
   :alt: **Figure 1** Process

   **Figure 1** Process

Prerequisites
-------------

A CDM cluster is available.

Creating an Agent
-----------------

#. Access the CDM console and choose **Cluster Management** in the left navigation pane. Locate the target cluster, choose **Job Management** > **Agent Management** > **Create Agent**, and configure agent parameters.


   .. figure:: /_static/images/en-us_image_0000001373408013.png
      :alt: **Figure 2** Creating an agent

      **Figure 2** Creating an agent

   -  **IP Address**: Set this parameter to the IP address of the server where the agent is deployed on the source network.
   -  **Port**: custom port of the agent Recommended value range: 1024-65535.
   -  **Enable Compression**: whether to compress data using the gzip algorithm.

      -  Enable this function for text data (data based on character encoding, such as MySQL INT data) because such data can be well compressed by the gzip algorithm. (For details about text data, see the related database documentation.)
      -  Disable this function for binary data (data based on value encoding, such as MySQL BINARY data) because such data has been compressed, and compressing it again will increase the workload to decompress data and undermine the performance of the client. (For details about text data, see the related database documentation.)

   -  **Enable SSL**: whether to enable two-way SSL authentication Enable this function if security is of high priority.
   -  **Bandwidth Throttling**: set the maximum downstream rate of the agent. By default, there is no throttling.

#. Click **OK**. On the **Agent Management** page, view the created agent.

Installing and Starting an Agent
--------------------------------

#. On the **Agent Management** page, locate the created agent and click **Download** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000001321928304.png
      :alt: **Figure 3** Downloading an agent

      **Figure 3** Downloading an agent

#. Prepare the server for installing the agent. The host has no special requirements for vCPUs, memory, and disks, but must meet the following requirements:

   -  Java 8 (64-bit) has been installed and Java environment variables have been configured.
   -  User **Ruby** must be granted the write permission of the **/tmp** directory. If there is no user **Ruby**, create one.

#. Upload the downloaded agent package to the server.

#. Decompress the package and run the following command to install the agent:

   **sh sbin/install.sh**

#. If you want to use the agent to connect to a relational database, you need to upload the corresponding drivers (see :ref:`Managing Drivers <dataartsstudio_01_0132>`) to the **/server/jdbc** directory in the agent installation directory and modify the version number of the corresponding database driver in the **properties** file in the same directory.

#. After the installation is complete, run the following commands to start the agent:

   **su Ruby**

   **sh sbin/start.sh**

#. Run the following command to check whether the agent is started:

   **ps -ef \| grep agent**

   If the command output contains the running agent process, the agent process has been started.

.. _dataartsstudio_01_0128__en-us_topic_0207402273_en-us_topic_0191978474_section1072083564713:

Connecting to an Agent
----------------------

#. On the **Agent Management** page, locate the created agent and click **Connect** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000001373288333.png
      :alt: **Figure 4** Connecting to an agent

      **Figure 4** Connecting to an agent

#. After the agent is successfully connected, you can select it when creating a connection.
