:original_name: dataartsstudio_03_0507.html

.. _dataartsstudio_03_0507:

Why Doesn't the Table in the Database Change After I Have Modified Fields in an ER or Dimensional Model?
========================================================================================================

Possible Causes
---------------

The table in the database does not change after the fields in an ER or dimensional model are modified.

Solution
--------

This is because the **Data Table Update Mode** parameter is not configured. Its default value is **No update**.

To configure the table update mode, perform the following steps:

#. On the DataArts Studio console, locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Architecture**.
#. On the DataArts Architecture page, choose **Configuration Center** in the left navigation pane.
#. Click the **Functions** tab.
#. Set **Data Table Update Mode** to **DDL-based update** or **Drop and create**.

   -  **No update**: The system does not update tables in a database.

   -  **DDL-based update**: The system updates tables in the database based on the DDL update template configured in DDL template management. The underlying data warehouse engine determines whether the update is successful. Different types of data warehouses support different table update modes. If the data warehouse does not support table update operations on the DataArts Architecture page, the tables in the database may be inconsistent with those in DataArts Architecture. For example, table fields cannot be deleted when DLI tables are updated. If table fields are deleted from the tables in DataArts Architecture, the corresponding table fields cannot be deleted from the database.

      If the offline database supports the syntax for updating the table architecture, you can configure the syntax in the DDL template. Then, the update operation can be managed on DataArts Studio. Otherwise, update the table by rebuilding it.

   -  **Drop and create**: The system deletes an existing table in a database and then creates a table. This option ensures that the tables in the database are the same as those in DataArts Architecture. However, since the table is deleted first, you are advised to select this option only in the development and design phase or test phase. After the product is brought online, you are not advised to select this option.

#. Click **OK**.
