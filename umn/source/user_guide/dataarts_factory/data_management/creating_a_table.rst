:original_name: dataartsstudio_01_0416.html

.. _dataartsstudio_01_0416:

Creating a Table
================

You can create a table on the DataArts Factory console, in DDL mode, or using a SQL script.

-  (Recommended) Console: You can directly create a table on the DataArts Studio DataArts Factory console with no code.
-  (Recommended) DDL mode: You can select the DDL mode in DataArts Studio's DataArts Factory module to create a table using a SQL script.
-  SQL script: You can also develop and execute a SQL script for creating a table in the SQL editor of DataArts Studio's DataArts Factory module or a data lake product, and then use the script to create a table.

This section describes how to create a table on the DataArts Factory console and in DDL mode.

Prerequisites
-------------

-  You have created a database and a DWS database schema. For details, see :ref:`Creating a Database <dataartsstudio_01_0405>` and :ref:`(Optional) Creating a Database Schema <dataartsstudio_01_0412>`.
-  A data connection that matches the table type has been created in DataArts Factory. For details, see :ref:`Creating a Data Connection <dataartsstudio_01_0404>`.

Creating a Table (GUI Mode)
---------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script development menu, click |image1|, expand the data connection to **tables**, and right-click **Create Table** or click |image2| to create a table.

#. In the displayed dialog box, configure parameters based on :ref:`Table 1 <dataartsstudio_01_0416__en-us_topic_0125513554_table168445103311>` on the **Basic property configuration** tab page.

   .. _dataartsstudio_01_0416__en-us_topic_0125513554_table168445103311:

   .. table:: **Table 1** Basic property parameters

      +----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection Type | Description                                                                                                                          |
      +======================+======================================================================================================================================+
      | DLI                  | For details, see the **Basic Property** part in :ref:`Table 5 <dataartsstudio_01_0416__en-us_topic_0125513554_table50275875142857>`. |
      +----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | GaussDB(DWS)         | For details, see the **Basic Property** part in :ref:`Table 6 <dataartsstudio_01_0416__en-us_topic_0125513554_table1834312173120>`.  |
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
      | GaussDB(DWS)         | For details, see the **Table Structure** part in :ref:`Table 6 <dataartsstudio_01_0416__en-us_topic_0125513554_table1834312173120>`.  |
      +----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Hive             | For details, see the **Table Structure** part in :ref:`Table 7 <dataartsstudio_01_0416__en-us_topic_0125513554_table122615115615>`.   |
      +----------------------+---------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Creating a Table (DDL Mode)
---------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script development menu, click |image3|, expand the data connection to **tables**, and right-click **Create Table** or click |image4| to create a table.

#. Click **DDL-based Table Creation** and enter SQL statements in the displayed editor. (Default values are set for the parameters listed in :ref:`Table 3 <dataartsstudio_01_0416__en-us_topic_0125513555_table1129115213117>`.) The following is an example:

   .. code-block::

      CREATE TABLE userinfo ( id INT, name STRING);

   .. note::

      The SQL syntax varies depending on the data source. Before developing an SQL statement, learn about the syntax of the data source from its documentation.

   .. _dataartsstudio_01_0416__en-us_topic_0125513555_table1129115213117:

   .. table:: **Table 3** Data table parameters

      ==================== ==================================================
      Parameter            Description
      ==================== ==================================================
      Data Connection Type Type of data connection to which the table belongs
      Data Connection      Data connection to which the table belongs
      Database             Database where the data table is located
      ==================== ==================================================

#. Click **Save**.

Related Operations
------------------

-  View table details: In the script development menu, click |image5|. Expand the data connection to the data table level, right-click a table name, and select **View Details** from the shortcut menu to view the table details shown in :ref:`Table 4 <dataartsstudio_01_0416__en-us_topic_0125513556_table2952161015324>`.

   .. _dataartsstudio_01_0416__en-us_topic_0125513556_table2952161015324:

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
      | DDL               | Displays the DDL of the DLI, DWS or MRS Hive data table.                |
      +-------------------+-------------------------------------------------------------------------+

-  Delete a table: In the script development menu, click |image6|. Expand a data connection, right-click a table name, select **Delete**, and click **OK** in the displayed dialog box.

   .. note::

      Deleted tables cannot be recovered. Exercise caution when performing this operation.

Parameter Description
---------------------

.. _dataartsstudio_01_0416__en-us_topic_0125513554_table50275875142857:

.. table:: **Table 5** DLI data table

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                |
   +=======================+=======================+============================================================================================================================================================================================================================================================================+
   | **Basic Property**    |                       |                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Name            | Yes                   | Name of a table. It can contain only letters, digits, and underscores (_). It cannot contain only digits or start with an underscore (_) or a digit.                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Alias                 | No                    | Alias of the data table. It can contain only letters, digits, and underscores (_). It cannot contain only digits or start with an underscore (_).                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection Type  | Yes                   | Type of the data connection to which the table belongs. The default value is used and cannot be changed.                                                                                                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection       | Yes                   | Data connection to which the table belongs. The default value is used and cannot be changed.                                                                                                                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database              | Yes                   | Database where the data table is located. The default value is used and cannot be changed.                                                                                                                                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Location         | Yes                   | Location to save data. Possible values:                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                            |
   |                       |                       | -  OBS                                                                                                                                                                                                                                                                     |
   |                       |                       | -  DLI                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Format           | Yes                   | Format of data. This parameter is available only when **Data Location** is set to **OBS**. Possible values:                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                            |
   |                       |                       | -  **parquet**: DataArts Factory can read non-compressed parquet data and parquet data compressed using Snappy or gzip.                                                                                                                                                    |
   |                       |                       | -  **csv**: DataArts Factory can read non-compressed CSV data and CSV data compressed using gzip.                                                                                                                                                                          |
   |                       |                       | -  **orc**: DataArts Factory can read non-compressed ORC data and ORC data compressed using Snappy.                                                                                                                                                                        |
   |                       |                       | -  **json**: DataArts Factory can read non-compressed JSON data and JSON data compressed using gzip.                                                                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Path                  | Yes                   | OBS path where the data is stored. This parameter is available only when **Data Location** is set to **OBS**.                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                            |
   |                       |                       | If no OBS path or OBS bucket is available, the system automatically creates an OBS directory.                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                            |
   |                       |                       | .. note::                                                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                            |
   |                       |                       |    If the number of OBS buckets has reached the upper limit, the system automatically displays the following message: "Failed to create the OBS directory. Error cause: [Create OBS Bucket failed:TooManyBuckets:You have attempted to create more buckets than allowed]". |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Description     | No                    | Descriptive information about the table.                                                                                                                                                                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Table Structure**   |                       |                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Type           | Yes                   | Type of the column. Available options include **Partition Column** and **Common Column**. The default value is **Common Column**.                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Name           | Yes                   | Name of the column. The name must be unique.                                                                                                                                                                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                  | Yes                   | Type of data.                                                                                                                                                                                                                                                              |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Description    | No                    | Descriptive information about the column.                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation             | No                    | To add a column, click |image7|.                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                            |
   |                       |                       | To delete a column, click |image8|.                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0416__en-us_topic_0125513554_table1834312173120:

.. table:: **Table 6** DWS data table

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================================================================================================+
   | **Basic Property**    |                       |                                                                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Name            | Yes                   | Name of a table. It can contain only letters, digits, and underscores (_). It cannot contain only digits or start with an underscore (_) or a digit.                                                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Alias                 | No                    | Alias of the data table. It can contain only letters, digits, and underscores (_). It cannot contain only digits or start with an underscore (_).                                                                                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection Type  | Yes                   | Type of the data connection to which the table belongs. The default value is used and cannot be changed.                                                                                                                                                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection       | Yes                   | Data connection to which the table belongs. The default value is used and cannot be changed.                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database              | Yes                   | Database where the data table is located. The default value is used and cannot be changed.                                                                                                                                                                                                                       |
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
   | Operation             | No                    | To add a column, click |image9|.                                                                                                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | To delete a column, click |image10|.                                                                                                                                                                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0416__en-us_topic_0125513554_table122615115615:

.. table:: **Table 7** MRS Hive data table

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================+
   | **Basic Property**    |                       |                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Name            | Yes                   | Name of a table. It can contain only letters, digits, and underscores (_). It cannot contain only digits or start with an underscore (_) or a digit. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Alias                 | No                    | Alias of the data table. It can contain only letters, digits, and underscores (_). It cannot contain only digits or start with an underscore (_).    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection Type  | Yes                   | Type of the data connection to which the table belongs. The default value is used and cannot be changed.                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection       | Yes                   | Data connection to which the table belongs. The default value is used and cannot be changed.                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database              | Yes                   | Database to which the table belongs. The default value is used and cannot be changed.                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table Description     | No                    | Descriptive information about the table.                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Table Structure**   |                       |                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Name           | Yes                   | Name of the column. The name must be unique.                                                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Classification   | Yes                   | Classification of data. Possible values:                                                                                                             |
   |                       |                       |                                                                                                                                                      |
   |                       |                       | -  Original type                                                                                                                                     |
   |                       |                       | -  ARRAY                                                                                                                                             |
   |                       |                       | -  MAP                                                                                                                                               |
   |                       |                       | -  STRUCT                                                                                                                                            |
   |                       |                       | -  UNION                                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Type             | Yes                   | Type of data. See `LanguageManual DDL <https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DDL#LanguageManualDDL-PartitionedTables>`__.  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Column Description    | No                    | Descriptive information about the column.                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation             | No                    | To add a column, click |image11|.                                                                                                                    |
   |                       |                       |                                                                                                                                                      |
   |                       |                       | To delete a column, click |image12|.                                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002234080764.png
.. |image2| image:: /_static/images/en-us_image_0000002234240616.png
.. |image3| image:: /_static/images/en-us_image_0000002269119985.png
.. |image4| image:: /_static/images/en-us_image_0000002269200033.png
.. |image5| image:: /_static/images/en-us_image_0000002269119953.png
.. |image6| image:: /_static/images/en-us_image_0000002234080788.png
.. |image7| image:: /_static/images/en-us_image_0000002234240612.png
.. |image8| image:: /_static/images/en-us_image_0000002234240632.png
.. |image9| image:: /_static/images/en-us_image_0000002234240612.png
.. |image10| image:: /_static/images/en-us_image_0000002234080752.png
.. |image11| image:: /_static/images/en-us_image_0000002234240612.png
.. |image12| image:: /_static/images/en-us_image_0000002269119961.png
