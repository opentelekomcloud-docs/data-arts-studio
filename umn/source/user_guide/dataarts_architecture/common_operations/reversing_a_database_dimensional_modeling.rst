:original_name: dataartsstudio_01_0610.html

.. _dataartsstudio_01_0610:

Reversing a Database (Dimensional Modeling)
===========================================

You can import tables from databases of other data sources to a specific model.

Prerequisites
-------------

You have collected metadata from databases in DataArts Catalog so that the system can synchronize tables to DataArts Catalog later. Otherwise, the synchronization tasks may fail. See :ref:`Configuring a Metadata Collection Task <dataartsstudio_01_0804>` for details.

Importing a Table to a Model by Reversing the Database
------------------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. On the DataArts Architecture page, choose **Models** > **Dimensional Modeling** in the left navigation pane.

#. Click the dimension or table tab, select a dimension or table from the drop-down list, and click **Reverse Database** above the list.


   .. figure:: /_static/images/en-us_image_0000002234244916.png
      :alt: **Figure 1** Selecting an object

      **Figure 1** Selecting an object

#. In the **Reverse Database** dialog box, set the parameters.

   .. table:: **Table 1** Parameters for reversing a database

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================================+
      | Subject                           | Select a subject from the drop-down list box.                                                                                                                                                                                                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection Type              | Type of the database to reverse.                                                                                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection                   | The name of the data connection.                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | If you want to reverse a database from other data sources to an ER model, you must create a data connection in Management Center to connect to the data source. For details on how to create data connections, see :ref:`Configuring DataArts Studio Data Connection Parameters <dataartsstudio_01_0009>`. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Database                          | The name of the database. Select a database from the drop-down list box.                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Queue                             | This parameter is displayed only for DLI data connections. Select a DLI queue.                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Schema                            | DWS or POSTGRESQL mode. This parameter is displayed only for DWS and POSTGRESQL data connections.                                                                                                                                                                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Update Existing Table             | The import operation can be used to create a table or update an existing table. It does not delete a table.                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | -  **No**: If you select this option, the existing tables will not be updated.                                                                                                                                                                                                                             |
      |                                   | -  **Yes**: If you select this option, the existing tables will be updated. If a table is in the **Published** state, you must publish the table again after updating it so that the updated table can take effect.                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name Source                       | Source of the table name or field name after the reverse. The value can be **Description** or **Name**. If no description is specified for a table or field, the name is used.                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | -  Description                                                                                                                                                                                                                                                                                             |
      |                                   | -  Name                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   |    .. note::                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   |       If you select **Description**, field comments of a table must be unique.                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Table                        | If you select **All**, all tables in the database are imported.                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | If you select **Partial**, not all tables in the database are imported.                                                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Yes** to start reversing the database. After the operation is complete, you can view the result on the **Last Reverse** tab page or perform the reverse operation again.
