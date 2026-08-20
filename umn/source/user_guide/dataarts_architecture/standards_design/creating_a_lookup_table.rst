:original_name: dataartsstudio_01_0604.html

.. _dataartsstudio_01_0604:

Creating a Lookup Table
=======================

A lookup table is also called a data dictionary table. It consists of enumerable data names and codes and stores the relationships between them. A lookup table provides the following functions:

-  Standardizes business data and supplements mapping fields during data cleansing.
-  Monitors the value range of business data during data quality monitoring.
-  Enumerates dimensions during dimensional modeling.

Creating and Publishing a Lookup Table
--------------------------------------

Manually create a lookup table. You can also add table records after creating a lookup table. For details, see :ref:`Filling in a Lookup Table <dataartsstudio_01_0604__section1775021114542>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. On the DataArts Architecture page, choose **Standards** > **Lookup Tables** in the left navigation pane.

#. Select a directory from the directory tree on the **Lookup Tables** page, and then click |image1| to create a directory under the selected directory. When creating a directory for the first time, you can create a directory under the root directory.


   .. figure:: /_static/images/en-us_image_0000002269121253.png
      :alt: **Figure 1** Lookup Tables page

      **Figure 1** Lookup Tables page

#. In the dialog box displayed, set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269201313.png
      :alt: **Figure 2** Create Directory dialog box

      **Figure 2** Create Directory dialog box

   .. table:: **Table 1** Directory parameters

      +--------------------+-------------------------------------------------------------------+
      | Parameter          | Description                                                       |
      +====================+===================================================================+
      | \*Name             | The following characters are not allowed: / \\ < > .              |
      +--------------------+-------------------------------------------------------------------+
      | \*Select Directory | Select an existing directory, and create a subdirectory under it. |
      +--------------------+-------------------------------------------------------------------+

#. Select the directory you created in the directory tree and click **Add** to create a lookup table.

#. On the **Create Lookup Table** page displayed, configure the parameters.

   In the **Table Details** area, set the parameters.


   .. figure:: /_static/images/en-us_image_0000002234241956.png
      :alt: **Figure 3** Table Details area

      **Figure 3** Table Details area

   .. table:: **Table 2** Parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================+
      | \*Table Name                      | Name of the lookup table to create.                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                   |
      |                                   | Newline characters and the following characters are not allowed: \\ < > % " ' ;                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Table Code                      | The code of the lookup table to create. You can select **Auto Generate** or **Custom** (enter a custom code). It must start with a letter. Only letters, digits, and underscores (_) are allowed. |
      |                                   |                                                                                                                                                                                                   |
      |                                   | The system can automatically generate the table code through translation based on a configured naming dictionary.                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the lookup table. Up to 600 characters are supported.                                                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   In the **Field Inputs** area, click **Add** or |image2| to add new fields, and click |image3| to delete unnecessary fields.


   .. figure:: /_static/images/en-us_image_0000002269201389.png
      :alt: **Figure 4** Field Inputs area

      **Figure 4** Field Inputs area

#. Click **Publish**. In the **Apply for Publication** dialog box displayed, select a reviewer and click **OK**. After the application is approved, the **Lookup Tables** page is displayed. You can view the created lookup table in the list, and the status of the table is **Published**. Only published lookup tables can be used.

   .. note::

      If you have been added as a reviewer, you can select **Auto-review** and click **OK**. After the application is approved, the lookup table status changes to **Published**.

      If you select multiple reviewers, the logical entities will be published only after all reviewers have approved the publishing request. If any reviewer rejects the request, the logical entities will not be published.

.. _dataartsstudio_01_0604__section1775021114542:

Filling in a Lookup Table
-------------------------

Input values in the created lookup tables.

#. On the DataArts Architecture page, choose **Standards** > **Lookup Tables** in the left navigation pane.

#. In the list of lookup tables, find the target table and choose **More** > **Manage Value** in the **Operation** column.

#. On the page displayed, click **Add**. In the dialog box displayed, set the parameters.


   .. figure:: /_static/images/en-us_image_0000002234241932.png
      :alt: **Figure 5** Inputting a value

      **Figure 5** Inputting a value

#. Click **OK**. You can also click **Continue** to add more records.

Importing a Lookup
------------------

You can import a new lookup table or import lookup table records in batches to an existing lookup table. If you have a large number of lookup table records, you are advised to import them in batches.

#. On the DataArts Architecture page, choose **Standards** > **Lookup Tables** in the left navigation pane.

#. On the page displayed, select a directory, and choose **More** > **Import**. You can also right-click the selected directory and choose **Import**.


   .. figure:: /_static/images/en-us_image_0000002269121301.png
      :alt: **Figure 6** Lookup Tables page

      **Figure 6** Lookup Tables page

#. In the **Import Lookup Table** dialog box displayed, set the parameters, and click **Upload**.


   .. figure:: /_static/images/en-us_image_0000002234082056.png
      :alt: **Figure 7** Import Lookup Table dialog box

      **Figure 7** Import Lookup Table dialog box

   .. table:: **Table 3** Parameters for importing a lookup table

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================================================================+
      | \*Update Table                    | Whether to update the existing lookup table. When a lookup table is imported, the system checks whether the lookup table exists according to its code. The options are as follows:                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | -  **No**: If you select this option, the existing lookup table will not be updated.                                                                                                                                                                                                                    |
      |                                   | -  **Yes**: If you select this option, the existing lookup table will be updated. If a lookup table is in the **Published** state, you must publish the lookup table again after updating it so that the updated lookup table can take effect.                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | The import can create a lookup table or update an existing lookup table. It will not delete a lookup table.                                                                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Upload File                     | Select the file to import. You can use either of the following methods to obtain the file to import:                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | -  **Downloading the lookup table template and filling in it**                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   |    In the **Import Lookup Table** dialog box, click **Lookup Table Template** to download the template, fill in the content, and save the settings. See :ref:`Table 4 <dataartsstudio_01_0604__table85831368219>` for template parameter details.                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   |    Instructions for filling in the lookup table template:                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   |    -  Parameters whose names start with an asterisk (*) are mandatory, and other parameters are optional.                                                                                                                                                                                               |
      |                                   |    -  Multiple fields can be added to a lookup table.                                                                                                                                                                                                                                                   |
      |                                   |    -  To import multiple lookup tables, you can add multiple sheets to the template file. The sheet name can be the lookup table name or code.                                                                                                                                                          |
      |                                   |    -  If the name of a lookup table already exists and **Update Table** is set to **Yes**, the existing lookup table will be updated during the import.                                                                                                                                                 |
      |                                   |    -  If the table name does not exist, a lookup table with that name is created during the import.                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | -  **Exporting lookup tables to files**                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   |    You can export the lookup tables created in DataArts Architecture of a DataArts Studio instance to an Excel file. Then, import the Excel file. For details on how to export lookup tables, see :ref:`Managing a Lookup Table <dataartsstudio_01_0604__en-us_topic_0189613897_section1941514304119>`. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dataartsstudio_01_0604__table85831368219:

   .. table:: **Table 4** Parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================+
      | Directory                         | The directory that a lookup table belongs to. Multi-level directories are separated with slashes (/), for example, **dir01/dir02**.                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Table Name                      | The name of the lookup table to create. Newline characters and the following characters are not allowed: \\ < > % " ' ;                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Table Code                      | The code of the lookup table to create. Only letters, numbers, and underscores (_) are allowed. A table code must start with a letter.                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Table Description                 | A description of the lookup table. Up to 600 characters are supported.                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Field Name                      | The name of a field. Field names must start with letters. Only letters, numbers, spaces, and the following special characters are allowed: ()-\_                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Field English Name              | Field name in English. Only letters, numbers, and underscores (_) are allowed. A field code must start with a letter.                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Field Data Type                 | The possible values are **STRING**, **BIGINT**, **DOUBLE**, **TIMESTAMP**, **DATE**, **BOOLEAN**, and **DECIMAL**.                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Field Description                 | The supplementary information about a field. Up to 600 characters are supported.                                                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Generate Standard                 | -  **true** indicates to generate a data standard.                                                                                                                                    |
      |                                   | -  **false** indicates not to generate a data standard. The default value is **false**.                                                                                               |
      |                                   |                                                                                                                                                                                       |
      |                                   | Note: To enable automatic generation of the data standard, choose **Configuration Center** in the navigation pane, click the **Standard Templates** tab, and select **Lookup table**. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   If the lookup table records need to be imported, create a sheet named by the lookup table name or code in the template and add table fields to the sheet. Each field occupies a column. The column name includes the code and value. Enter the lookup table values to be imported. If the template contains a sheet named after the lookup table, you do not need to create the sheet. You can directly enter the table values to be imported in the sheet.

   .. note::

      If a sheet name is too long, it will be automatically truncated.

#. View the import result on the **Last Import** tab page. If the import is successful, click **Close**. If the import fails, you can view the failure cause, correct the template file, and upload it again.

Importing a Lookup Table Through a Reverse Database
---------------------------------------------------

With reverse databases, you can import one or more created database tables from other data sources into a lookup table directory to turn them into lookup tables.

#. On the DataArts Architecture page, choose **Standards** > **Lookup Tables** in the left navigation pane.

#. On the page displayed, select a directory and click **Reverse Database** above the lookup table list.

#. In the dialog box displayed, set the parameters and click **OK**.

   .. table:: **Table 5** Parameters for reversing a database

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================================================+
      | \*Data Connection Type            | The data connection types supported by the reverse database are displayed in the drop-down list box. Select the required data connection type.                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | Select a data connection.                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                            |
      |                                   | If you want to reverse a database from other data sources to a lookup table directory, you must create a data connection in Management Center to connect to the data source. For details on how to create data connections, see :ref:`Configuring DataArts Studio Data Connection Parameters <dataartsstudio_01_0009>`.    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Database                        | The name of the database. Select a database from the drop-down list box.                                                                                                                                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Schema                          | Select a value from the drop-down list box. This parameter is available only for DWS and PostgreSQL tables.                                                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Queue                             | DLI queue. This parameter is available only when **Data Connection Type** is set to **DLI**.                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Update Table                      | When **Yes** is selected, if the name of the reversed table is the same as that of an existing table in the lookup table list, the existing table is updated.                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name Source                       | Source of the table name or field name after the reverse. The value can be **Description** or **Name**. If no description is specified for a table or field, the name is used.                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  Description                                                                                                                                                                                                                                                                                                             |
      |                                   | -  Name                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                            |
      |                                   |    .. note::                                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                            |
      |                                   |       If you select **Description**, field comments of a table must be unique.                                                                                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Reverse Table                     | -  **No**: If you select this option, tables are imported to the lookup table directory but table data is not imported during database reverse. After reversing a database, you can add records to the lookup table. Refer to :ref:`Filling in a Lookup Table <dataartsstudio_01_0604__section1775021114542>` for details. |
      |                                   | -  **Overwrite**: If you select this option, tables are imported to the lookup table directory and table data is imported as well during database reverse.                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Table                      | You can select one or more data tables to import.                                                                                                                                                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. You can view the result on the **Last Reverse** tab page. If the reverse operation is successful, click **Close**. If the reverse operation fails, you can view the failure cause. After the fault is rectified, select the table again and click **Reverse** to retry.


   .. figure:: /_static/images/en-us_image_0000002234241872.png
      :alt: **Figure 8** Last Reverse tab page

      **Figure 8** Last Reverse tab page

Exporting a Lookup Table
------------------------

When exporting a lookup table, ensure that the table name contains no more than 32 characters.

#. On the DataArts Architecture page, choose **Standards** > **Lookup Tables** in the left navigation pane.
#. Export a lookup table.

   -  **Export a single lookup table.**

      In the lookup table list, select the target lookup table and choose **More** > **Export**.


      .. figure:: /_static/images/en-us_image_0000002234082108.png
         :alt: **Figure 9** Lookup table list

         **Figure 9** Lookup table list

   -  **Export all tables in the list.**

      Right-click a directory in the directory tree and choose **Export**.


      .. figure:: /_static/images/en-us_image_0000002269201369.png
         :alt: **Figure 10** Directories storing exported lookup tables

         **Figure 10** Directories storing exported lookup tables

Deleting a Lookup Table
-----------------------

Deleted lookup tables cannot be recovered. Exercise caution when performing this operation. A lookup table in publishing review, published, or suspension review state cannot be deleted.

#. On the DataArts Architecture page, choose **Standards** > **Lookup Tables** in the left navigation pane.
#. In the lookup table list, select the target lookup table and choose **More** > **Delete** above the list.
#. In the dialog box displayed, click **Yes**.

Deleting a Lookup Table Directory
---------------------------------

A directory or its subdirectories that contain a lookup table cannot be deleted. You must delete the lookup table before deleting the directory.

#. On the DataArts Architecture page, choose **Standards** > **Lookup Tables** in the left navigation pane.

#. Right-click a directory in the directory tree and choose **Delete**.


   .. figure:: /_static/images/en-us_image_0000002234082072.png
      :alt: **Figure 11** Managing lookup table directories

      **Figure 11** Managing lookup table directories

#. In the dialog box displayed, click **Yes**.

.. _dataartsstudio_01_0604__en-us_topic_0189613897_section1941514304119:

Managing a Lookup Table
-----------------------

You can query, edit, suspend, or publish a lookup table.

On the DataArts Architecture page, choose **Standards** > **Lookup Tables** in the left navigation pane. You can manage the lookup tables as required.

.. note::

   -  The lookup tables created in the **public workspace** can be queried in a common workspace, but the lookup tables created in a common workspace cannot be queried in the **public workspace**.
   -  A common workspace has the edit permission of only the lookup tables and directories created in the same workspace, and can view indexes in the **public workspace** rather than perform any operation on the lookup tables and directories in the **public workspace**.


.. figure:: /_static/images/en-us_image_0000002234241914.png
   :alt: **Figure 12** Managing lookup tables

   **Figure 12** Managing lookup tables

-  **Edit**

   In the lookup table list, select a table you want to edit and click **Edit** in the **Operation** column.

-  **Publish**

   In the lookup table list, click **Publish** in a row containing a table in the **Draft** or **Rejected** state, select a reviewer in the dialog box displayed, and click **OK**. After the application is approved, the lookup table is published. If you have been added as a reviewer, you can select **Auto-review** and click **OK**. After the application is approved, the lookup table status changes to **Published**.

-  **Suspend**

   In the lookup table list, locate a published lookup table you want to suspend, click **More** in the **Operation** column, and select **Suspend** from the drop-down list. In the displayed dialog box, select a reviewer and click **OK**. After the application is approved, the lookup table is suspended.

-  **Manage Value**

   In the lookup table list, locate a lookup table, click **More** in the **Operation** column, and select **Manage Value** from the drop-down list. Then you can edit the value of each field.

-  **View History**

   In the lookup table list, locate a lookup table, click **More** in the **Operation** column, and select **View History** from the drop-down list. Then you can view the publish history and changes of the lookup table, and compare different versions of it.

.. |image1| image:: /_static/images/en-us_image_0000002234241896.png
.. |image2| image:: /_static/images/en-us_image_0000002234082128.png
.. |image3| image:: /_static/images/en-us_image_0000002269121341.png
