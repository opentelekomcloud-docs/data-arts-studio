:original_name: dataartsstudio_01_0524.html

.. _dataartsstudio_01_0524:

Developing a DWS SQL Job
========================

This section describes how to use the DWS SQL operator to develop a job on DataArts Factory.

Scenario
--------

This tutorial describes how to develop a DWS job to collect the sales volume of a store on the previous day.

Preparing the Environment
-------------------------

-  Enable DWS and create a DWS cluster for running DWS SQL jobs.

-  Enable CDM incremental packages and create a CDM cluster.

   Ensure that the VPC, subnet, and security group of the CDM cluster are the same as those of the DWS cluster so that the two clusters can communicate with each other.

.. _dataartsstudio_01_0524__en-us_topic_0127305016_section1033111569439:

Creating a DWS Data Connection
------------------------------

Before developing a DWS SQL job, you must create a data connection to DWS on the **Manage Data Connections** page of **Management Center**. The data connection name is **dws_link**.

The key parameters are as follows:

-  **Cluster Name**: Select the DWS cluster you have created when preparing the environment.
-  **Agent**: Select the CDM cluster you have created when preparing the environment.

Creating a Database
-------------------

Create a **gaussdb** database by following the instructions in :ref:`Creating a Database <dataartsstudio_01_0405>`.

Creating Data Tables
--------------------

Create tables **trade_log** and **trade_report** in the **gaussdb** database. The following is an example script for creating the tables:

.. code-block::

   create schema store_sales;
   set current_schema= store_sales;
   drop table if exists trade_log;
   CREATE TABLE trade_log
   (
           sn           VARCHAR(16),
           trade_time   DATE,
           trade_count   INTEGER(8)
   );
   set current_schema= store_sales;
   drop table if exists trade_report;
   CREATE TABLE trade_report
   (
           rq   DATE,
           trade_total   INTEGER(8)
   );

.. _dataartsstudio_01_0524__en-us_topic_0127305016_section17888155820591:

Developing a DWS SQL Script
---------------------------

Choose **Development** > **Develop Script** and create a DWS SQL script named **dws_sql**. Enter an SQL statement in the editor to collect the sales amount of the previous day.

.. _dataartsstudio_01_0524__en-us_topic_0127305016_fig693875618223:

.. figure:: /_static/images/en-us_image_0000001373168993.png
   :alt: **Figure 1** Developing a script

   **Figure 1** Developing a script

Key notes:

-  The script development area in :ref:`Figure 1 <dataartsstudio_01_0524__en-us_topic_0127305016_fig693875618223>` is a temporary debugging area. After you close the script tab, the development area will be cleared. You can click **Submit** to save and submit a script version.
-  **Connection**: Select the data connection created in :ref:`Creating a DWS Data Connection <dataartsstudio_01_0524__en-us_topic_0127305016_section1033111569439>`.


Developing a DWS SQL Job
------------------------

After developing the DWS SQL script, create a job for periodically executing the DWS SQL script.

#. Create an empty job named **job_dws_sql**.


   .. figure:: /_static/images/en-us_image_0000001373408377.png
      :alt: **Figure 2** Creating the job_dws_sql job

      **Figure 2** Creating the job_dws_sql job

#. Go to the job development page, drag the DWS SQL node to the canvas, and click the node to configure its properties.


   .. figure:: /_static/images/en-us_image_0000001373088181.png
      :alt: **Figure 3** Configuring properties for the DWS SQL node

      **Figure 3** Configuring properties for the DWS SQL node

   Key properties:

   -  **SQL script**: Associate with the **dws_sql** script developed in :ref:`Developing a DWS SQL Script <dataartsstudio_01_0524__en-us_topic_0127305016_section17888155820591>`.

   -  **Data Connection**: Select the data connection configured in the **dws_sql** script. The data connection can be changed.

   -  **Database**: Select the database configured in the **dws_sql** script. The database can be changed.

   -  **Script Parameter**: Obtain the value of **yesterday** using the following EL expression:

      .. code-block::

         #{Job.getYesterday("yyyy-MM-dd")}

   -  **Node Name**: The name of the **dws_sql** script is displayed by default. The name can be changed.

#. After configuring the job, click |image1| to test it.

#. If the test is successful, click the blank area on the canvas and then the **Scheduling Setup** tab on the right. On the displayed page, configure the scheduling policy.


   .. figure:: /_static/images/en-us_image_0000001322088348.png
      :alt: **Figure 4** Configuring the scheduling policy

      **Figure 4** Configuring the scheduling policy

   Parameter descriptions:

   From Aug 6 to Aug 31 in 2021, the job was executed once at 02:00 every day.

#. Click **Submit** and then **Execute**. The job will be executed automatically every day.

.. |image1| image:: /_static/images/en-us_image_0000001322408244.png
