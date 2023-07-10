:original_name: dataartsstudio_01_0461.html

.. _dataartsstudio_01_0461:

ETL Job
=======

Functions
---------

The ETL Job node is used to extract data from a specified data source, preprocess the data, and import the data to the target data source.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0461__en-us_topic_0163990343_table3764823994826>`, :ref:`Table 2 <dataartsstudio_01_0461__en-us_topic_0163990343_table1768155103511>`, and :ref:`Table 3 <dataartsstudio_01_0461__en-us_topic_0114569494_table987664914213>` describe the parameters of the ETL Job node.

.. _dataartsstudio_01_0461__en-us_topic_0163990343_table3764823994826:

.. table:: **Table 1** Parameters of Transform Load nodes

   +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory             | Description                                                                                                                                                                                                                           |
   +========================+=======================+=======================================================================================================================================================================================================================================+
   | Node Name              | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>).                                               |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ETL Configuration      | Yes                   | Click |image1| to edit the source and destination data to be transformed.                                                                                                                                                             |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       | The supported source data types are DLI, OBS and MySQL.                                                                                                                                                                               |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       | -  When the source data type is DLI, the supported destination data types are DWS, GES, CSS, OBS, and DLI.                                                                                                                            |
   |                        |                       | -  When the source data type is MySQL, the supported destination data type is MySQL.                                                                                                                                                  |
   |                        |                       | -  When the source data type is OBS, the supported destination data can be of the DLI type and the DWS type.                                                                                                                          |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       | .. important::                                                                                                                                                                                                                        |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       |    NOTICE:                                                                                                                                                                                                                            |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       |    -  Data transformation from DLI to DWS:                                                                                                                                                                                            |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       |       Before importing data from DataArts Factory to DWS, ensure that a DWS data connection and a table have been created.                                                                                                            |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       |       Before importing data from DLI to DWS, ensure that a DWS table have been created.                                                                                                                                               |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       |    -  Data transformation from DLI to CSS:                                                                                                                                                                                            |
   |                        |                       |                                                                                                                                                                                                                                       |
   |                        |                       |       Before importing data from DLI to CSS, ensure that a cross-source connection associated with CSS has been created on DLI. For details about how to create a cross-source connection on DLI, see *Data Lake Insight User Guide*. |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configure SQL Template | No                    | Click **Obtain Template** to obtain an SQL template.                                                                                                                                                                                  |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0461__en-us_topic_0163990343_table1768155103511:

.. table:: **Table 2** Advanced parameters

   +------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Mandatory             | Description                                                                                                                                                                                 |
   +==============================+=======================+=============================================================================================================================================================================================+
   | Max. Node Execution Duration | Yes                   | Execution timeout interval for the node. If retry is configured and the execution is not complete within the timeout interval, the node will not be retried and is set to the failed state. |
   +------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Retry upon Failure           | Yes                   | Indicates whether to re-execute a node task if its execution fails. Possible values:                                                                                                        |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       | -  **Yes**: The node task will be re-executed, and the following parameters must be configured:                                                                                             |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       |    -  **Maximum Retries**                                                                                                                                                                   |
   |                              |                       |    -  **Retry Interval (seconds)**                                                                                                                                                          |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       | -  **No**: The node task will not be re-executed. This is the default setting.                                                                                                              |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       | .. note::                                                                                                                                                                                   |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       |    If **Timeout Interval** is configured for the node, the node will not be executed again after the execution times out. Instead, the node is set to the failure state.                    |
   +------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure Policy               | Yes                   | Operation that will be performed if the node task fails to be executed. Possible values:                                                                                                    |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       | -  **End the current job execution plan**: stops running the current job. The job instance status is **Failed**.                                                                            |
   |                              |                       | -  **Go to the next node**: ignores the execution failure of the current node. The job instance status is **Failure ignored**.                                                              |
   |                              |                       | -  **Suspend current job execution plan**: suspends running the current job. The job instance status is **Waiting**.                                                                        |
   |                              |                       | -  **Suspend execution plans of the subsequent nodes**: stops running subsequent nodes. The job instance status is **Failed**.                                                              |
   +------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0461__en-us_topic_0114569494_table987664914213:

.. table:: **Table 3** Lineage

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                 |
   +===================================+=============================================================================================================================================================+
   | **Input**                         |                                                                                                                                                             |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add                               | Click **Add**. In the **Type** drop-down list, select the type to be created. The value can be **DWS**, **OBS**, **CSS**, **HIVE**, **DLI**, or **CUSTOM**. |
   |                                   |                                                                                                                                                             |
   |                                   | -  DWS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image2|. In the displayed dialog box, select a DWS data connection.                                                       |
   |                                   |    -  **Database**: Click |image3|. In the displayed dialog box, select a DWS database.                                                                     |
   |                                   |    -  **Schema**: Click |image4|. In the displayed dialog box, select a DWS schema.                                                                         |
   |                                   |    -  **Table Name**: Click |image5|. In the displayed dialog box, select a DWS table.                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   | -  OBS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Path**: Click |image6|. In the displayed dialog box, select an OBS path.                                                                            |
   |                                   |                                                                                                                                                             |
   |                                   | -  CSS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Cluster Name**: Click |image7|. In the displayed dialog box, select a CSS cluster.                                                                  |
   |                                   |    -  **Index**: Enter a CSS index name.                                                                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  HIVE                                                                                                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image8|. In the displayed dialog box, select a HIVE data connection.                                                      |
   |                                   |    -  **Database**: Click |image9|. In the displayed dialog box, select a HIVE database.                                                                    |
   |                                   |    -  **Table Name**: Click |image10|. In the displayed dialog box, select a HIVE table.                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  CUSTOM                                                                                                                                                   |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Name**: Enter a name of the CUSTOM type.                                                                                                            |
   |                                   |    -  **Attribute**: Enter an attribute of the CUSTOM type. You can add more than one attribute.                                                            |
   |                                   |                                                                                                                                                             |
   |                                   | -  DLI                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image11|. In the displayed dialog box, select a DLI data connection.                                                      |
   |                                   |    -  **Database**: Click |image12|. In the displayed dialog box, select a DLI database.                                                                    |
   |                                   |    -  **Table Name**: Click |image13|. In the displayed dialog box, select a DLI table.                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK                                | Click **OK** to save the parameter settings.                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel                            | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                            | Click |image14| to modify the parameter settings. After the modification, save the settings.                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                            | Click |image15| to delete the parameter settings.                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details                      | Click |image16| to view details about the table created based on the input lineage.                                                                         |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Output**                        |                                                                                                                                                             |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add                               | Click **Add**. In the **Type** drop-down list, select the type to be created. The value can be **DWS**, **OBS**, **CSS**, **HIVE**, **DLI**, or **CUSTOM**. |
   |                                   |                                                                                                                                                             |
   |                                   | -  DWS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image17|. In the displayed dialog box, select a DWS data connection.                                                      |
   |                                   |    -  **Database**: Click |image18|. In the displayed dialog box, select a DWS database.                                                                    |
   |                                   |    -  **Schema**: Click |image19|. In the displayed dialog box, select a DWS schema.                                                                        |
   |                                   |    -  **Table Name**: Click |image20|. In the displayed dialog box, select a DWS table.                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   | -  OBS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Path**: Click |image21|. In the displayed dialog box, select an OBS path.                                                                           |
   |                                   |                                                                                                                                                             |
   |                                   | -  CSS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Cluster Name**: Click |image22|. In the displayed dialog box, select a CSS cluster.                                                                 |
   |                                   |    -  **Index**: Enter a CSS index name.                                                                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  HIVE                                                                                                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image23|. In the displayed dialog box, select a HIVE data connection.                                                     |
   |                                   |    -  **Database**: Click |image24|. In the displayed dialog box, select a HIVE database.                                                                   |
   |                                   |    -  **Table Name**: Click |image25|. In the displayed dialog box, select a HIVE table.                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  CUSTOM                                                                                                                                                   |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Name**: Enter a name of the CUSTOM type.                                                                                                            |
   |                                   |    -  **Attribute**: Enter an attribute of the CUSTOM type. You can add more than one attribute.                                                            |
   |                                   |                                                                                                                                                             |
   |                                   | -  DLI                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image26|. In the displayed dialog box, select a DLI data connection.                                                      |
   |                                   |    -  **Database**: Click |image27|. In the displayed dialog box, select a DLI database.                                                                    |
   |                                   |    -  **Table Name**: Click |image28|. In the displayed dialog box, select a DLI table.                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK                                | Click **OK** to save the parameter settings.                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel                            | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                            | Click |image29| to modify the parameter settings. After the modification, save the settings.                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                            | Click |image30| to delete the parameter settings.                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details                      | Click |image31| to view details about the table created based on the output lineage.                                                                        |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001322088448.png
.. |image2| image:: /_static/images/en-us_image_0000001373288685.png
.. |image3| image:: /_static/images/en-us_image_0000001322088340.png
.. |image4| image:: /_static/images/en-us_image_0000001373168981.png
.. |image5| image:: /_static/images/en-us_image_0000001373088173.png
.. |image6| image:: /_static/images/en-us_image_0000001322088336.png
.. |image7| image:: /_static/images/en-us_image_0000001322088332.png
.. |image8| image:: /_static/images/en-us_image_0000001322408220.png
.. |image9| image:: /_static/images/en-us_image_0000001322248236.png
.. |image10| image:: /_static/images/en-us_image_0000001373168965.png
.. |image11| image:: /_static/images/en-us_image_0000001373168969.png
.. |image12| image:: /_static/images/en-us_image_0000001373288673.png
.. |image13| image:: /_static/images/en-us_image_0000001321928640.png
.. |image14| image:: /_static/images/en-us_image_0000001373408357.png
.. |image15| image:: /_static/images/en-us_image_0000001322088324.png
.. |image16| image:: /_static/images/en-us_image_0000001373288669.png
.. |image17| image:: /_static/images/en-us_image_0000001322408216.png
.. |image18| image:: /_static/images/en-us_image_0000001322248228.png
.. |image19| image:: /_static/images/en-us_image_0000001373408349.png
.. |image20| image:: /_static/images/en-us_image_0000001322408212.png
.. |image21| image:: /_static/images/en-us_image_0000001322088320.png
.. |image22| image:: /_static/images/en-us_image_0000001373408373.png
.. |image23| image:: /_static/images/en-us_image_0000001373088169.png
.. |image24| image:: /_static/images/en-us_image_0000001373288689.png
.. |image25| image:: /_static/images/en-us_image_0000001373168973.png
.. |image26| image:: /_static/images/en-us_image_0000001373408369.png
.. |image27| image:: /_static/images/en-us_image_0000001322408228.png
.. |image28| image:: /_static/images/en-us_image_0000001322248244.png
.. |image29| image:: /_static/images/en-us_image_0000001322248240.png
.. |image30| image:: /_static/images/en-us_image_0000001373168977.png
.. |image31| image:: /_static/images/en-us_image_0000001373288677.png
