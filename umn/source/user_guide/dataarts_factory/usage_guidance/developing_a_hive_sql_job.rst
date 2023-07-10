:original_name: dataartsstudio_01_0522.html

.. _dataartsstudio_01_0522:

Developing a Hive SQL Job
=========================

This section introduces how to develop Hive SQL scripts on DataArts Factory.

**Scenario Description**
------------------------

As a one-stop big data development platform, DataArts Factory supports development of multiple big data tools. Hive is a data warehouse tool running on Hadoop. It can map structured data files to a database table and provides a simple SQL search function that converts SQL statements into MapReduce tasks.

Preparations
------------

-  MRS has been enabled and an MRS cluster has been created for running Hive SQL jobs.

   The MRS cluster must contain the Hive component.

-  Cloud Data Migration (CDM) has been enabled and a CDM cluster has been created for providing an agent for communication between DataArts Factory and MRS.

   Ensure that the VPC, subnet, and security group of the CDM cluster are the same as those of the MRS cluster so that the two clusters can communicate with each other.

.. _dataartsstudio_01_0522__en-us_topic_0127305016_section1033111569439:

Creating a Hive Data Connection
-------------------------------

Before developing a Hive SQL script, you must create a data connection to MRS Hive on the **Manage Data Connections** page of **Management Center**. The data connection name is **hive1009**.

Description of key parameters:

-  **Cluster Name**: Enter the name of the created MRS cluster.
-  **Agent**: Select the created CDM cluster.

.. _dataartsstudio_01_0522__en-us_topic_0127305016_section17888155820591:

Developing a Hive SQL Script
----------------------------

Choose **Development** > **Develop Script** and create a Hive SQL script named **hive_sql**. Then enter SQL statements in the editor to fulfill business requirements.

.. _dataartsstudio_01_0522__en-us_topic_0127305016_fig693875618223:

.. figure:: /_static/images/en-us_image_0000001322247900.png
   :alt: **Figure 1** Developing a script

   **Figure 1** Developing a script

Notes:

-  The script development area in :ref:`Figure 1 <dataartsstudio_01_0522__en-us_topic_0127305016_fig693875618223>` is a temporary debugging area. After you close the tab page, the development area will be cleared. You can click **Submit** to save and submit a script version.
-  Data Connection: Connection created in :ref:`Creating a Hive Data Connection <dataartsstudio_01_0522__en-us_topic_0127305016_section1033111569439>`.


Developing a Hive SQL Job
-------------------------

After the Hive SQL script is developed, build a periodically deducted job for the Hive SQL script so that the script can be executed periodically.

#. Create an empty DataArts Factory job named **job_hive_sql**.


   .. figure:: /_static/images/en-us_image_0000001322407888.png
      :alt: **Figure 2** Creating a job named job_hive_sql

      **Figure 2** Creating a job named job_hive_sql

#. Go to the job development page, drag the MRS Hive SQL node to the canvas, and click the node to configure node properties.


   .. figure:: /_static/images/en-us_image_0000001322088000.png
      :alt: **Figure 3** Configuring properties for an MRS Hive SQL node

      **Figure 3** Configuring properties for an MRS Hive SQL node

   Description of key properties:

   -  SQL Script: Hive SQL script **hive_sql** that is developed in :ref:`Developing a Hive SQL Script <dataartsstudio_01_0522__en-us_topic_0127305016_section17888155820591>`.
   -  Data Connection: Data connection that is configured in the SQL script **hive_sql** is selected by default. The value can be changed.
   -  Database: Database that is configured in the SQL script **hive_sql** and is selected by default. The value can be changed.
   -  Node Name: Name of the SQL script **hive_sql** by default. The value can be changed.

#. After configuring the job, click |image1| to test it.

#. If the job runs successfully, click the blank area on the canvas and configure the job scheduling policy on the scheduling configuration page on the right.


   .. figure:: /_static/images/en-us_image_0000001321928316.png
      :alt: **Figure 4** Configuring the scheduling mode

      **Figure 4** Configuring the scheduling mode

   Note:

   From Jan 1 to Jan 25 in 2021, the job was executed at 02:00 every day.

#. Click **Submit** and **Execute**. The job will be automatically executed every day.

.. |image1| image:: /_static/images/en-us_image_0000001373087837.png
