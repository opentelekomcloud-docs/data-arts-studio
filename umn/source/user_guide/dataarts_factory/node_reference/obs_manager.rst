:original_name: dataartsstudio_01_0464.html

.. _dataartsstudio_01_0464:

OBS Manager
===========

Constraints
-----------

This function depends on OBS.

Function
--------

The OBS Manager node is used to move or copy files from an OBS bucket to a specified directory.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0464__en-us_topic_0156398631_table3764823994826>`, :ref:`Table 2 <dataartsstudio_01_0464__en-us_topic_0156398631_table58040457102411>`, and :ref:`Table 3 <dataartsstudio_01_0464__en-us_topic_0114569494_table987664914213>` describe the parameters of the OBS Managernode node.

.. _dataartsstudio_01_0464__en-us_topic_0156398631_table3764823994826:

.. table:: **Table 1** Parameters of OBS Manager nodes

   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory             | Description                                                                                                                                                                                                                                                        |
   +==========================+=======================+====================================================================================================================================================================================================================================================================+
   | Node Name                | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>).                                                                            |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation Type           | Yes                   | Operations that can be performed on the node.                                                                                                                                                                                                                      |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       | -  **Move File**: moves a source file or directory to a new directory.                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       | -  **Copy File**: copies the source file or directory.                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       | -  **Rename File**: renames the last level of the directory or file.                                                                                                                                                                                               |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       |    For example, you can rename the directory **obs://test/a/b/c/** as **obs://test/a/b/d/**, and rename the file **obs://test/a/b/hello.txt** as **obs://test/a/b/bye.txt**.                                                                                       |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       | -  **Monitor File**: checks whether a file or directory exists. If the file or directory exists, the node is executed successfully. Otherwise, the node fails to be executed.                                                                                      |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Source File or Directory | Yes                   | OBS file or directory to be managed in the OBS bucket.                                                                                                                                                                                                             |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Target Directory         | Yes                   | Directory for storing OBS files to be moved or copied from the OBS bucket.                                                                                                                                                                                         |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | File Filter              | No                    | Wildcard for file filtering. Only the files that meet the filtering condition can be moved or copied. If this parameter is not specified, all source files are moved by default. For example, when you enter \*.csv, files in this format will be moved or copied. |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0464__en-us_topic_0156398631_table58040457102411:

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

.. _dataartsstudio_01_0464__en-us_topic_0114569494_table987664914213:

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
   |                                   |    -  **Connection Name**: Click |image1|. In the displayed dialog box, select a DWS data connection.                                                       |
   |                                   |    -  **Database**: Click |image2|. In the displayed dialog box, select a DWS database.                                                                     |
   |                                   |    -  **Schema**: Click |image3|. In the displayed dialog box, select a DWS schema.                                                                         |
   |                                   |    -  **Table Name**: Click |image4|. In the displayed dialog box, select a DWS table.                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   | -  OBS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Path**: Click |image5|. In the displayed dialog box, select an OBS path.                                                                            |
   |                                   |                                                                                                                                                             |
   |                                   | -  CSS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Cluster Name**: Click |image6|. In the displayed dialog box, select a CSS cluster.                                                                  |
   |                                   |    -  **Index**: Enter a CSS index name.                                                                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  HIVE                                                                                                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image7|. In the displayed dialog box, select a HIVE data connection.                                                      |
   |                                   |    -  **Database**: Click |image8|. In the displayed dialog box, select a HIVE database.                                                                    |
   |                                   |    -  **Table Name**: Click |image9|. In the displayed dialog box, select a HIVE table.                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   | -  CUSTOM                                                                                                                                                   |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Name**: Enter a name of the CUSTOM type.                                                                                                            |
   |                                   |    -  **Attribute**: Enter an attribute of the CUSTOM type. You can add more than one attribute.                                                            |
   |                                   |                                                                                                                                                             |
   |                                   | -  DLI                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image10|. In the displayed dialog box, select a DLI data connection.                                                      |
   |                                   |    -  **Database**: Click |image11|. In the displayed dialog box, select a DLI database.                                                                    |
   |                                   |    -  **Table Name**: Click |image12|. In the displayed dialog box, select a DLI table.                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK                                | Click **OK** to save the parameter settings.                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel                            | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                            | Click |image13| to modify the parameter settings. After the modification, save the settings.                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                            | Click |image14| to delete the parameter settings.                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details                      | Click |image15| to view details about the table created based on the input lineage.                                                                         |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Output**                        |                                                                                                                                                             |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add                               | Click **Add**. In the **Type** drop-down list, select the type to be created. The value can be **DWS**, **OBS**, **CSS**, **HIVE**, **DLI**, or **CUSTOM**. |
   |                                   |                                                                                                                                                             |
   |                                   | -  DWS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image16|. In the displayed dialog box, select a DWS data connection.                                                      |
   |                                   |    -  **Database**: Click |image17|. In the displayed dialog box, select a DWS database.                                                                    |
   |                                   |    -  **Schema**: Click |image18|. In the displayed dialog box, select a DWS schema.                                                                        |
   |                                   |    -  **Table Name**: Click |image19|. In the displayed dialog box, select a DWS table.                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   | -  OBS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Path**: Click |image20|. In the displayed dialog box, select an OBS path.                                                                           |
   |                                   |                                                                                                                                                             |
   |                                   | -  CSS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Cluster Name**: Click |image21|. In the displayed dialog box, select a CSS cluster.                                                                 |
   |                                   |    -  **Index**: Enter a CSS index name.                                                                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  HIVE                                                                                                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image22|. In the displayed dialog box, select a HIVE data connection.                                                     |
   |                                   |    -  **Database**: Click |image23|. In the displayed dialog box, select a HIVE database.                                                                   |
   |                                   |    -  **Table Name**: Click |image24|. In the displayed dialog box, select a HIVE table.                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  CUSTOM                                                                                                                                                   |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Name**: Enter a name of the CUSTOM type.                                                                                                            |
   |                                   |    -  **Attribute**: Enter an attribute of the CUSTOM type. You can add more than one attribute.                                                            |
   |                                   |                                                                                                                                                             |
   |                                   | -  DLI                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image25|. In the displayed dialog box, select a DLI data connection.                                                      |
   |                                   |    -  **Database**: Click |image26|. In the displayed dialog box, select a DLI database.                                                                    |
   |                                   |    -  **Table Name**: Click |image27|. In the displayed dialog box, select a DLI table.                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK                                | Click **OK** to save the parameter settings.                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel                            | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                            | Click |image28| to modify the parameter settings. After the modification, save the settings.                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                            | Click |image29| to delete the parameter settings.                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details                      | Click |image30| to view details about the table created based on the output lineage.                                                                        |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001373288685.png
.. |image2| image:: /_static/images/en-us_image_0000001322088340.png
.. |image3| image:: /_static/images/en-us_image_0000001373168981.png
.. |image4| image:: /_static/images/en-us_image_0000001373088173.png
.. |image5| image:: /_static/images/en-us_image_0000001322088336.png
.. |image6| image:: /_static/images/en-us_image_0000001322088332.png
.. |image7| image:: /_static/images/en-us_image_0000001322408220.png
.. |image8| image:: /_static/images/en-us_image_0000001322248236.png
.. |image9| image:: /_static/images/en-us_image_0000001373168965.png
.. |image10| image:: /_static/images/en-us_image_0000001373168969.png
.. |image11| image:: /_static/images/en-us_image_0000001373288673.png
.. |image12| image:: /_static/images/en-us_image_0000001321928640.png
.. |image13| image:: /_static/images/en-us_image_0000001373408357.png
.. |image14| image:: /_static/images/en-us_image_0000001322088324.png
.. |image15| image:: /_static/images/en-us_image_0000001373288669.png
.. |image16| image:: /_static/images/en-us_image_0000001322408216.png
.. |image17| image:: /_static/images/en-us_image_0000001322248228.png
.. |image18| image:: /_static/images/en-us_image_0000001373408349.png
.. |image19| image:: /_static/images/en-us_image_0000001322408212.png
.. |image20| image:: /_static/images/en-us_image_0000001322088320.png
.. |image21| image:: /_static/images/en-us_image_0000001373408373.png
.. |image22| image:: /_static/images/en-us_image_0000001373088169.png
.. |image23| image:: /_static/images/en-us_image_0000001373288689.png
.. |image24| image:: /_static/images/en-us_image_0000001373168973.png
.. |image25| image:: /_static/images/en-us_image_0000001373408369.png
.. |image26| image:: /_static/images/en-us_image_0000001322408228.png
.. |image27| image:: /_static/images/en-us_image_0000001322248244.png
.. |image28| image:: /_static/images/en-us_image_0000001322248240.png
.. |image29| image:: /_static/images/en-us_image_0000001373168977.png
.. |image30| image:: /_static/images/en-us_image_0000001373288677.png
