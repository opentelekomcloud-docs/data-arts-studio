:original_name: dataartsstudio_01_0416.html

.. _dataartsstudio_01_0416:

Creating a Table
================

You can create a table on the DataArts Factory console, in DDL mode, or using a SQL script.

-  (Recommended) Console: You can directly create a table on the DataArts Studio DataArts Factory console with no code.
-  (Recommended) DDL mode: You can select the DDL mode in DataArts Studio's DataArts Factory mode to create a table using a SQL script.
-  SQL script: You can also develop and execute a SQL script for creating a table in the SQL editor of DataArts Studio's DataArts Factory module or a data lake product, and then use the script to create a table.

This section describes how to create a table on the DataArts Factory console and in DDL mode.

Prerequisites
-------------

-  A database has been created in the cloud service.
-  A data connection that matches the table type has been created in DataArts Factory. For details, see :ref:`Creating a Data Connection <dataartsstudio_01_0404>`.

Creating a Table (GUI Mode)
---------------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.

#. Choose |image1| from the menu on the left and expand the directory of a data connection to **tables** under **Data Connections**. Right-click **tables** and choose **Create Data Table** from the shortcut menu.

#. In the displayed dialog box, configure basic properties. Specific settings vary depending on the data connection type you select. :ref:`Table 1 <dataartsstudio_01_0416__en-us_topic_0125513554_table168445103311>` lists the links for viewing property parameters of each type of data connection.

   .. _dataartsstudio_01_0416__en-us_topic_0125513554_table168445103311:

   .. table:: **Table 1** Basic property parameters

      +----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection Type | Description                                                                                                                          |
      +======================+======================================================================================================================================+
      | DLI                  | For details, see the **Basic Property** part in :ref:`Table 5 <dataartsstudio_01_0416__en-us_topic_0125513554_table50275875142857>`. |
      +----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | DWS                  | For details, see the **Basic Property** part in :ref:`Table 6 <dataartsstudio_01_0416__en-us_topic_0125513554_table1834312173120>`.  |
      +----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Hive             | For details, see the **Basic Property** part in :ref:`Table 7 <dataartsstudio_01_0416__en-us_topic_0125513554_table122615115615>`.   |
      +----------------------+--------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next**. On the **Configure Table Structure** page, configure tbe table structure parameters based on :ref:`Table 2 <dataartsstudio_01_0416__en-us_topic_0125513554_table198753321147>`.

   .. _dataartsstudio_01_0416__en-us_topic_0125513554_table198753321147:

   .. table:: **Table 2** Table structure

      +----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection Type | Description                                                                                                                           |
      +======================+=======================================================================================================================================+
      | DLI                  | For details, see the **Table Structure** part in :ref:`Table 5 <dataartsstudio_01_0416__en-us_topic_0125513554_table50275875142857>`. |
      +----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | DWS                  | For details, see the **Table Structure** part in :ref:`Table 6 <dataartsstudio_01_0416__en-us_topic_0125513554_table1834312173120>`.  |
      +----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Hive             | For details, see the **Table Structure** part in :ref:`Table 7 <dataartsstudio_01_0416__en-us_topic_0125513554_table122615115615>`.   |
      +----------------------+---------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Creating a Table (DDL Mode)
---------------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.

#. Choose |image2| from the menu on the left and expand the directory of a data connection to **tables** under **Data Connections**. Right-click **tables** and choose **Create Data Table** from the shortcut menu.

#. Click **DDL-based Table Creation**, configure the parameters based on :ref:`Table 3 <dataartsstudio_01_0416__en-us_topic_0125513555_table1129115213117>`, and enter SQL statements in the editor in the lower part.

   .. _dataartsstudio_01_0416__en-us_topic_0125513555_table1129115213117:

   .. table:: **Table 3** Data table parameters

      +-----------------------------------+-----------------------------------------------------+
      | Parameter                         | Description                                         |
      +===================================+=====================================================+
      | Data Connection Type              | Type of data connection to which the table belongs. |
      |                                   |                                                     |
      |                                   | -  DLI                                              |
      |                                   | -  DWS                                              |
      |                                   | -  HIVE                                             |
      +-----------------------------------+-----------------------------------------------------+
      | Data Connection                   | Data connection to which the table belongs.         |
      +-----------------------------------+-----------------------------------------------------+
      | Database                          | Database to which the table belongs.                |
      +-----------------------------------+-----------------------------------------------------+

#. Click **OK**.

Viewing Table Details
---------------------

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.
#. Choose |image3| from the menu on the left and expand the directory of a data connection to a table name under **Data Connections**. Right-click the table name and choose **View Details** from the shortcut menu.
#. In the displayed dialog box, view the table information listed in |image4|.

   .. table:: **Table 4** Table details

      +-------------------+-------------------------------------------------------------------------+
      | Tab Name          | Description                                                             |
      +===================+=========================================================================+
      | Table Information | Displays the basic information and storage information about the table. |
      +-------------------+-------------------------------------------------------------------------+
      | Field Information | Displays the field information about the table.                         |
      +-------------------+-------------------------------------------------------------------------+
      | Data Preview      | Displays 10 records in the table.                                       |
      +-------------------+-------------------------------------------------------------------------+
      | DDL               | Displays the DDL of the DWS, DLI, or MRS Hive data table.               |
      +-------------------+-------------------------------------------------------------------------+

Viewing Table Column Details
----------------------------

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.
#. Choose |image5| from the menu on the left and expand the data connection directory to view column information under a desired table.

Deleting a Table
----------------

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.
#. Choose |image6| from the menu on the left and expand the directory of a data connection to a table name under **Data Connections**. Right-click the table name and choose **Delete** from the shortcut menu.
#. In the **Delete Data Table** dialog box, click **OK**.

Parameter Description
---------------------

.. _dataartsstudio_01_0416__en-us_topic_0125513554_table50275875142857:

.. table:: **Table 5** DLI data table

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                            |
   +=======================+=======================+========================================================================================================================================================================================+
   | **Basic Property**    |                       |                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Name            | Yes                   | Name of a table. The name must contain 1 to 63 characters, including only lowercase letters, numbers, and underscores (_). It cannot contain only numbers or start with an underscore. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Alias                 | No                    | Alias of a table. The alias must contain 1 to 63 characters, including only letters, numbers, and underscores (_). It cannot contain only numbers or start with an underscore.         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection       | Yes                   | Data connection to which the table belongs.                                                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database              | Yes                   | Database to which the table belongs.                                                                                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Location         | Yes                   | Location to save data. Possible values:                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | -  OBS                                                                                                                                                                                 |
   |                       |                       | -  DLI                                                                                                                                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Format           | Yes                   | Format of data. This parameter is available only when **Data Location** is set to **OBS**. Possible values:                                                                            |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | -  **parquet**: DLF can read non-compressed parquet data and parquet data compressed using Snappy or gzip.                                                                             |
   |                       |                       | -  **csv**: DLF can read non-compressed CSV data and CSV data compressed using gzip.                                                                                                   |
   |                       |                       | -  **orc**: DLF can read non-compressed ORC data and ORC data compressed using Snappy.                                                                                                 |
   |                       |                       | -  **json**: DLF can read non-compressed JSON data and JSON data compressed using gzip.                                                                                                |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Path                  | Yes                   | OBS path where the data is stored. This parameter is available only when **Data Location** is set to **OBS**.                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Description     | No                    | Descriptive information about the table.                                                                                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Table Structure**   |                       |                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Name           | Yes                   | Name of the column. The name must be unique.                                                                                                                                           |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                  | Yes                   | Type of data.                                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Description    | No                    | Descriptive information about the column.                                                                                                                                              |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation             | No                    | To add a column, click |image7|.                                                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0416__en-us_topic_0125513554_table1834312173120:

.. table:: **Table 6** DWS data table

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================================================================================================+
   | **Basic Property**    |                       |                                                                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Name            | Yes                   | Name of a table. The name must contain 1 to 63 characters, including only letters, numbers, and underscores (_). It cannot contain only numbers or start with an underscore.                                                                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Alias                 | No                    | Alias of a table. The alias must contain 1 to 63 characters, including only letters, numbers, and underscores (_). It cannot contain only numbers or start with an underscore.                                                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection       | Yes                   | Data connection to which the table belongs.                                                                                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database              | Yes                   | Database to which the table belongs.                                                                                                                                                                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Schema                | Yes                   | Schema of the database.                                                                                                                                                                                                                                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Description     | No                    | Descriptive information about the table.                                                                                                                                                                                                                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Advanced Settings     | No                    | The following advanced options are available:                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  Storage method of a table. Possible values:                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       |    -  **Row store**                                                                                                                                                                                                                                                                                              |
   |                       |                       |    -  **Column store**                                                                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  Compression level of a table                                                                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       |    -  Available values when the storage method is row store: **YES** or **NO**.                                                                                                                                                                                                                                  |
   |                       |                       |    -  Available values when the storage method is column store: **YES**, **NO**, **LOW**, **MIDDLE**, or **HIGH**. For the same compression level in column store mode, you can configure compression grades from 0 to 3. Within any compression level, the higher the grade, the greater the compression ratio. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Table Structure**   |                       |                                                                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Name           | Yes                   | Name of the column. The name must be unique.                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Classification   | Yes                   | Classification of data. Possible values:                                                                                                                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **Value**                                                                                                                                                                                                                                                                                                     |
   |                       |                       | -  **Currency**                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **Boolean**                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Binary**                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **Character**                                                                                                                                                                                                                                                                                                 |
   |                       |                       | -  **Time**                                                                                                                                                                                                                                                                                                      |
   |                       |                       | -  **Geometric**                                                                                                                                                                                                                                                                                                 |
   |                       |                       | -  **Network address**                                                                                                                                                                                                                                                                                           |
   |                       |                       | -  **Bit string**                                                                                                                                                                                                                                                                                                |
   |                       |                       | -  **Text search**                                                                                                                                                                                                                                                                                               |
   |                       |                       | -  **UUID**                                                                                                                                                                                                                                                                                                      |
   |                       |                       | -  **JSON**                                                                                                                                                                                                                                                                                                      |
   |                       |                       | -  **OID**                                                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Type             | Yes                   | Type of data.                                                                                                                                                                                                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Description    | No                    | Descriptive information about the column.                                                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Create ES Index       | No                    | If you click the check box, an ES index needs to be created. When creating the ES index, select the created CSS cluster from the **CloudSearch Cluster Name** drop-down list. For details about how to create a CSS cluster, see *Cloud Search Service User Guide*.                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Index Data Type       | No                    | Data type of the ES index. The options are as follows:                                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  text                                                                                                                                                                                                                                                                                                          |
   |                       |                       | -  keyword                                                                                                                                                                                                                                                                                                       |
   |                       |                       | -  date                                                                                                                                                                                                                                                                                                          |
   |                       |                       | -  long                                                                                                                                                                                                                                                                                                          |
   |                       |                       | -  integer                                                                                                                                                                                                                                                                                                       |
   |                       |                       | -  short                                                                                                                                                                                                                                                                                                         |
   |                       |                       | -  byte                                                                                                                                                                                                                                                                                                          |
   |                       |                       | -  double                                                                                                                                                                                                                                                                                                        |
   |                       |                       | -  boolean                                                                                                                                                                                                                                                                                                       |
   |                       |                       | -  binary                                                                                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation             | No                    | To add a column, click |image8|.                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0416__en-us_topic_0125513554_table122615115615:

.. table:: **Table 7** Basic property parameters of an MRS Hive data table

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                            |
   +=======================+=======================+========================================================================================================================================================================================+
   | **Basic Property**    |                       |                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Name            | Yes                   | Name of a table. The name must contain 1 to 63 characters, including only lowercase letters, numbers, and underscores (_). It cannot contain only numbers or start with an underscore. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Alias                 | No                    | Alias of a table. The alias must contain 1 to 63 characters, including only letters, numbers, and underscores (_). It cannot contain only numbers or start with an underscore.         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection       | Yes                   | Data connection to which the table belongs.                                                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database              | Yes                   | Database to which the table belongs.                                                                                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Description     | No                    | Descriptive information about the table.                                                                                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Table Structure**   |                       |                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Name           | Yes                   | Name of the column. The name must be unique.                                                                                                                                           |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Classification   | Yes                   | Classification of data. Possible values:                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                        |
   |                       |                       | -  Original type                                                                                                                                                                       |
   |                       |                       | -  ARRAY                                                                                                                                                                               |
   |                       |                       | -  MAP                                                                                                                                                                                 |
   |                       |                       | -  STRUCT                                                                                                                                                                              |
   |                       |                       | -  UNION                                                                                                                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Type             | Yes                   | Type of data. See `LanguageManual DDL <https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DDL#LanguageManualDDL-PartitionedTables>`__.                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Description    | No                    | Descriptive information about the column.                                                                                                                                              |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation             | No                    | To add a column, click |image9|.                                                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001322247912.png
.. |image2| image:: /_static/images/en-us_image_0000001373288385.png
.. |image3| image:: /_static/images/en-us_image_0000001322247940.png
.. |image4| image:: /_static/images/en-us_image_0000001322247940.png
.. |image5| image:: /_static/images/en-us_image_0000001373168681.png
.. |image6| image:: /_static/images/en-us_image_0000001322407932.png
.. |image7| image:: /_static/images/en-us_image_0000001373408073.png
.. |image8| image:: /_static/images/en-us_image_0000001373408073.png
.. |image9| image:: /_static/images/en-us_image_0000001373408073.png
