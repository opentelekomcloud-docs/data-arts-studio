:original_name: dataartsstudio_01_1584.html

.. _dataartsstudio_01_1584:

Obtaining the Maximum Value and Transferring It to a CDM Job Using a Query SQL Statement
========================================================================================

Scenario
--------

You can run a query SQL statement to transfer the obtained maximum time value to a CDM job. In the advanced attributes of the CDM job, the where clause is used to determine the maximum time range to obtain the data to be migrated and complete the incremental data migration.

Constraints
-----------

#. You have completed operations in :ref:`Creating a Data Connection <dataartsstudio_01_0404>`.
#. You have completed operations in :ref:`Creating a Database <dataartsstudio_01_0405>`.

Examples
--------

**Creating an SQL Script**

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. Create an SQL script. This section uses the MRS Spark SQL script as an example.

#. Select a created data connection and database.

#. Compile the SQL script to obtain the maximum time data from table1.

   .. code-block::

      select max(time) from table1

#. Save and submit the version. The **maxtime** script is created.

**Creating a Pipeline Subjob**

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. Select a CDM Job node and configure the node properties.


   .. figure:: /_static/images/en-us_image_0000002234079008.png
      :alt: **Figure 1** Configuring CDM Job node properties

      **Figure 1** Configuring CDM Job node properties

   Select a CDM cluster and associate the node with an existing CDM job.

   Configure the job parameters and add job parameter **maxtime**.


   .. figure:: /_static/images/en-us_image_0000002234238852.png
      :alt: **Figure 2** Configuring job parameters

      **Figure 2** Configuring job parameters

#. Save and submit the version. The subjob **sub** is created.

**Creating a Pipeline Job**

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. Select an MRS Spark SQL node and a For Each node to execute the CDM subjob cyclically.

#. Configure properties of the MRS Spark SQL node and associate the node with the created **maxtime** script.


   .. figure:: /_static/images/en-us_image_0000002234079016.png
      :alt: **Figure 3** Configuring properties for the MRS Spark SQL node

      **Figure 3** Configuring properties for the MRS Spark SQL node

#. Configure properties of the For Each node and associate the node with the created CDM subjob.


   .. figure:: /_static/images/en-us_image_0000002269118201.png
      :alt: **Figure 4** Configuring properties for the For Each node

      **Figure 4** Configuring properties for the For Each node

   After associating the node with the created subjob **sub**, write a parameter expression.

   .. code-block::

      #{Loop.current[0]}

   Configure the data set, with an EL expression supported.

   .. code-block::

      #{Job.getNodeOutput("maxtime")}

#. Save and submit the version. The job is created.

**Obtaining the Maximum Time Value from the CDM Job Using a Where Clause and Transferring the Value to the Destination Job**

#. Open the created subjob.

#. Click |image1| next to the job name to go to the job configuration page.


   .. figure:: /_static/images/en-us_image_0000002269118193.png
      :alt: **Figure 5** Editing the CDM job

      **Figure 5** Editing the CDM job

#. In the advanced attributes of the source job configuration, configure a where clause to obtain the data to be migrated. When the job is executed, the migration data obtained from the source will be replicated, exported, and imported to the destination.


   .. figure:: /_static/images/en-us_image_0000002234079000.png
      :alt: **Figure 6** Configuring a where clause

      **Figure 6** Configuring a where clause

   The where clause is as follows:

   .. code-block::

      dt > '${maxtime}'

.. |image1| image:: /_static/images/en-us_image_0000002269198293.png
