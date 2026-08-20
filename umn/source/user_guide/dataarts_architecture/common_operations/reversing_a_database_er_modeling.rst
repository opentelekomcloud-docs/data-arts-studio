:original_name: dataartsstudio_01_0635.html

.. _dataartsstudio_01_0635:

Reversing a Database (ER Modeling)
==================================

You can import tables from databases of other data sources to a specific model.

Prerequisites
-------------

You have collected metadata from databases in DataArts Catalog so that the system can synchronize tables to DataArts Catalog later. Otherwise, the synchronization tasks may fail. See :ref:`Configuring a Metadata Collection Task <dataartsstudio_01_0804>` for details.

Importing a Table to a Model by Reversing the Database
------------------------------------------------------

#. On the DataArts Architecture page, choose **Models** > **ER Modeling** in the left navigation pane.

#. In the middle of the page, select a physical model from the drop-down list box on the top. Alternatively, click a physical model on the **Data Warehouse Layer** page to go to the physical table list page. Click **Reverse Database**.


   .. figure:: /_static/images/en-us_image_0000002269202025.png
      :alt: **Figure 1** Reverse Database dialog box

      **Figure 1** Reverse Database dialog box

#. In the **Reverse Database** dialog box, set the parameters.


   .. figure:: /_static/images/en-us_image_0000002269121977.png
      :alt: **Figure 2** Setting parameters for reversing the database

      **Figure 2** Setting parameters for reversing the database

   .. table:: **Table 1** Parameters for reversing a database

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================================+
      | \*Subject                         | Select a subject from the drop-down list box.                                                                                                                                                                                                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection Type              | If you reverse tables to a logical model, select a required data connection type from the drop-down list box.                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | If you reverse tables to a physical model, the data connection type of the current model is displayed.                                                                                                                                                                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection                   | The name of the data connection. Select the required data connection.                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | If you want to reverse a database from other data sources to an ER model, you must create a data connection in Management Center to connect to the data source. For details on how to create data connections, see :ref:`Configuring DataArts Studio Data Connection Parameters <dataartsstudio_01_0009>`. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Database                          | The name of the database. Select a database from the drop-down list box.                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Queue                             | This parameter is displayed only for DLI data connections. Select a DLI queue.                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Schema                            | Select a value from the drop-down list box. This parameter is available only for DWS and PostgreSQL tables.                                                                                                                                                                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Update Table                      | Whether to update the existing table if the table to be imported already exists in the ER model. When a table is imported, the system checks whether the table exists according to the table code. During the import, only table creation and update are allowed.                                          |
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
      | Data Table                        | If you select **All**, all tables in the database are imported to the ER model.                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | If you select **Partial**, not all tables in the database are imported to the ER model.                                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Start Page                        | This parameter is mandatory when **Data Table** is set to **All**.                                                                                                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Yes** to start reversing the database.
