:original_name: dataartsstudio_01_0450.html

.. _dataartsstudio_01_0450:

DLI SQL
=======

Functions
---------

The DLI SQL node is used to transfer SQL statements to DLI for data source analysis and exploration.

Working Principles
------------------

This node enables you to execute DLI statements during periodical or real-time job scheduling. You can use parameter variables to perform incremental import and process partitions for your data warehouses.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0450__en-us_topic_0102588983_table3764823994826>`, :ref:`Table 2 <dataartsstudio_01_0450__en-us_topic_0102588983_table58040457102411>`, and :ref:`Table 3 <dataartsstudio_01_0450__en-us_topic_0114569494_table987664914213>` describe the parameters of the DLI SQLnode node.

.. _dataartsstudio_01_0450__en-us_topic_0102588983_table3764823994826:

.. table:: **Table 1** Parameters of DLI SQL nodes

   +----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Mandatory             | Description                                                                                                                                                                                                                       |
   +============================+=======================+===================================================================================================================================================================================================================================+
   | SQL Statement or Script    | Yes                   | You can select SQL statements or SQL scripts.                                                                                                                                                                                     |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       | -  SQL Statement                                                                                                                                                                                                                  |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       |    In the **SQL statement** text box, enter the SQL statement to be executed.                                                                                                                                                     |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       | -  SQL Script                                                                                                                                                                                                                     |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       |    Select a script to be executed. If the script is not created, create and develop the script by repeating steps :ref:`Creating a Script <dataartsstudio_01_0423>` and :ref:`Developing an SQL Script <dataartsstudio_01_0424>`. |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       |    .. note::                                                                                                                                                                                                                      |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       |       If you select the SQL statement mode, the DataArts Factory module cannot parse the parameters contained in the SQL statement.                                                                                               |
   +----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database Name              | Yes                   | Database that is configured in the SQL script. The value can be changed.                                                                                                                                                          |
   +----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DLI Environmental Variable | No                    | -  The environment variable must start with **dli.sql.** or **spark.sql.**                                                                                                                                                        |
   |                            |                       | -  If the key of the environment variable is **dli.sql.shuffle.partitions** or **dli.sql.autoBroadcastJoinThreshold**, the environment variable cannot contain the greater than (>) or less than (<) sign.                        |
   |                            |                       | -  If a parameter with the same name is configured in both a job and a script, the parameter value configured in the job will overwrite that configured in the script.                                                            |
   +----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Queue Name                 | Yes                   | Name of the DLI queue configured in the SQL script. The value can be changed.                                                                                                                                                     |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       | You can create a resource queue using either of the following methods:                                                                                                                                                            |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       | -  Click |image1|. On the **Queue Management** page of DLI, create a resource queue.                                                                                                                                              |
   |                            |                       | -  Go to the DLI console to create a resource queue.                                                                                                                                                                              |
   +----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Script Parameter           | No                    | If the associated SQL script uses a parameter, the parameter name is displayed. Set the parameter value in the text box next to the parameter name. The parameter value can be :ref:`an EL expression <dataartsstudio_01_0494>`.  |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       | If the parameters of the associated SQL script are changed, click |image2| to refresh the parameters.                                                                                                                             |
   +----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Node Name                  | Yes                   | Name of the SQL script. The value can be changed. The rules are as follows:                                                                                                                                                       |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>).                                           |
   +----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Record Dirty Data          | Yes                   | Click |image3| to specify whether to record dirty data.                                                                                                                                                                           |
   |                            |                       |                                                                                                                                                                                                                                   |
   |                            |                       | -  If you select |image4|, dirty data will be recorded.                                                                                                                                                                           |
   |                            |                       | -  If you do not select |image5|, dirty data will not be recorded.                                                                                                                                                                |
   +----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0450__en-us_topic_0102588983_table58040457102411:

.. table:: **Table 2** Advanced parameters

   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                        | Mandatory             | Description                                                                                                                                                                                 |
   +==================================+=======================+=============================================================================================================================================================================================+
   | Node Status Polling Interval (s) | Yes                   | Specifies how often the system check completeness of the node task. The value ranges from 1 to 60 seconds.                                                                                  |
   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. Node Execution Duration     | Yes                   | Execution timeout interval for the node. If retry is configured and the execution is not complete within the timeout interval, the node will not be retried and is set to the failed state. |
   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Retry upon Failure               | Yes                   | Indicates whether to re-execute a node task if its execution fails. Possible values:                                                                                                        |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       | -  **Yes**: The node task will be re-executed, and the following parameters must be configured:                                                                                             |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       |    -  **Maximum Retries**                                                                                                                                                                   |
   |                                  |                       |    -  **Retry Interval (seconds)**                                                                                                                                                          |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       | -  **No**: The node task will not be re-executed. This is the default setting.                                                                                                              |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       | .. note::                                                                                                                                                                                   |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       |    If **Timeout Interval** is configured for the node, the node will not be executed again after the execution times out. Instead, the node is set to the failure state.                    |
   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure Policy                   | Yes                   | Operation that will be performed if the node task fails to be executed. Possible values:                                                                                                    |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       | -  **End the current job execution plan**: stops running the current job. The job instance status is **Failed**.                                                                            |
   |                                  |                       | -  **Go to the next node**: ignores the execution failure of the current node. The job instance status is **Failure ignored**.                                                              |
   |                                  |                       | -  **Suspend current job execution plan**: suspends running the current job. The job instance status is **Waiting**.                                                                        |
   |                                  |                       | -  **Suspend execution plans of the subsequent nodes**: stops running subsequent nodes. The job instance status is **Failed**.                                                              |
   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0450__en-us_topic_0114569494_table987664914213:

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
   |                                   |    -  **Connection Name**: Click |image6|. In the displayed dialog box, select a DWS data connection.                                                       |
   |                                   |    -  **Database**: Click |image7|. In the displayed dialog box, select a DWS database.                                                                     |
   |                                   |    -  **Schema**: Click |image8|. In the displayed dialog box, select a DWS schema.                                                                         |
   |                                   |    -  **Table Name**: Click |image9|. In the displayed dialog box, select a DWS table.                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   | -  OBS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Path**: Click |image10|. In the displayed dialog box, select an OBS path.                                                                           |
   |                                   |                                                                                                                                                             |
   |                                   | -  CSS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Cluster Name**: Click |image11|. In the displayed dialog box, select a CSS cluster.                                                                 |
   |                                   |    -  **Index**: Enter a CSS index name.                                                                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  HIVE                                                                                                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image12|. In the displayed dialog box, select a HIVE data connection.                                                     |
   |                                   |    -  **Database**: Click |image13|. In the displayed dialog box, select a HIVE database.                                                                   |
   |                                   |    -  **Table Name**: Click |image14|. In the displayed dialog box, select a HIVE table.                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  CUSTOM                                                                                                                                                   |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Name**: Enter a name of the CUSTOM type.                                                                                                            |
   |                                   |    -  **Attribute**: Enter an attribute of the CUSTOM type. You can add more than one attribute.                                                            |
   |                                   |                                                                                                                                                             |
   |                                   | -  DLI                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image15|. In the displayed dialog box, select a DLI data connection.                                                      |
   |                                   |    -  **Database**: Click |image16|. In the displayed dialog box, select a DLI database.                                                                    |
   |                                   |    -  **Table Name**: Click |image17|. In the displayed dialog box, select a DLI table.                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK                                | Click **OK** to save the parameter settings.                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel                            | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                            | Click |image18| to modify the parameter settings. After the modification, save the settings.                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                            | Click |image19| to delete the parameter settings.                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details                      | Click |image20| to view details about the table created based on the input lineage.                                                                         |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Output**                        |                                                                                                                                                             |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add                               | Click **Add**. In the **Type** drop-down list, select the type to be created. The value can be **DWS**, **OBS**, **CSS**, **HIVE**, **DLI**, or **CUSTOM**. |
   |                                   |                                                                                                                                                             |
   |                                   | -  DWS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image21|. In the displayed dialog box, select a DWS data connection.                                                      |
   |                                   |    -  **Database**: Click |image22|. In the displayed dialog box, select a DWS database.                                                                    |
   |                                   |    -  **Schema**: Click |image23|. In the displayed dialog box, select a DWS schema.                                                                        |
   |                                   |    -  **Table Name**: Click |image24|. In the displayed dialog box, select a DWS table.                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   | -  OBS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Path**: Click |image25|. In the displayed dialog box, select an OBS path.                                                                           |
   |                                   |                                                                                                                                                             |
   |                                   | -  CSS                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Cluster Name**: Click |image26|. In the displayed dialog box, select a CSS cluster.                                                                 |
   |                                   |    -  **Index**: Enter a CSS index name.                                                                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  HIVE                                                                                                                                                     |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image27|. In the displayed dialog box, select a HIVE data connection.                                                     |
   |                                   |    -  **Database**: Click |image28|. In the displayed dialog box, select a HIVE database.                                                                   |
   |                                   |    -  **Table Name**: Click |image29|. In the displayed dialog box, select a HIVE table.                                                                    |
   |                                   |                                                                                                                                                             |
   |                                   | -  CUSTOM                                                                                                                                                   |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Name**: Enter a name of the CUSTOM type.                                                                                                            |
   |                                   |    -  **Attribute**: Enter an attribute of the CUSTOM type. You can add more than one attribute.                                                            |
   |                                   |                                                                                                                                                             |
   |                                   | -  DLI                                                                                                                                                      |
   |                                   |                                                                                                                                                             |
   |                                   |    -  **Connection Name**: Click |image30|. In the displayed dialog box, select a DLI data connection.                                                      |
   |                                   |    -  **Database**: Click |image31|. In the displayed dialog box, select a DLI database.                                                                    |
   |                                   |    -  **Table Name**: Click |image32|. In the displayed dialog box, select a DLI table.                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK                                | Click **OK** to save the parameter settings.                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel                            | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                            | Click |image33| to modify the parameter settings. After the modification, save the settings.                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                            | Click |image34| to delete the parameter settings.                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details                      | Click |image35| to view details about the table created based on the output lineage.                                                                        |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001321928820.png
.. |image2| image:: /_static/images/en-us_image_0000001373088341.png
.. |image3| image:: /_static/images/en-us_image_0000001322408412.png
.. |image4| image:: /_static/images/en-us_image_0000001322408412.png
.. |image5| image:: /_static/images/en-us_image_0000001322408412.png
.. |image6| image:: /_static/images/en-us_image_0000001373288685.png
.. |image7| image:: /_static/images/en-us_image_0000001322088340.png
.. |image8| image:: /_static/images/en-us_image_0000001373168981.png
.. |image9| image:: /_static/images/en-us_image_0000001373088173.png
.. |image10| image:: /_static/images/en-us_image_0000001322088336.png
.. |image11| image:: /_static/images/en-us_image_0000001322088332.png
.. |image12| image:: /_static/images/en-us_image_0000001322408220.png
.. |image13| image:: /_static/images/en-us_image_0000001322248236.png
.. |image14| image:: /_static/images/en-us_image_0000001373168965.png
.. |image15| image:: /_static/images/en-us_image_0000001373168969.png
.. |image16| image:: /_static/images/en-us_image_0000001373288673.png
.. |image17| image:: /_static/images/en-us_image_0000001321928640.png
.. |image18| image:: /_static/images/en-us_image_0000001373408357.png
.. |image19| image:: /_static/images/en-us_image_0000001322088324.png
.. |image20| image:: /_static/images/en-us_image_0000001373288669.png
.. |image21| image:: /_static/images/en-us_image_0000001322408216.png
.. |image22| image:: /_static/images/en-us_image_0000001322248228.png
.. |image23| image:: /_static/images/en-us_image_0000001373408349.png
.. |image24| image:: /_static/images/en-us_image_0000001322408212.png
.. |image25| image:: /_static/images/en-us_image_0000001322088320.png
.. |image26| image:: /_static/images/en-us_image_0000001373408373.png
.. |image27| image:: /_static/images/en-us_image_0000001373088169.png
.. |image28| image:: /_static/images/en-us_image_0000001373288689.png
.. |image29| image:: /_static/images/en-us_image_0000001373168973.png
.. |image30| image:: /_static/images/en-us_image_0000001373408369.png
.. |image31| image:: /_static/images/en-us_image_0000001322408228.png
.. |image32| image:: /_static/images/en-us_image_0000001322248244.png
.. |image33| image:: /_static/images/en-us_image_0000001322248240.png
.. |image34| image:: /_static/images/en-us_image_0000001373168977.png
.. |image35| image:: /_static/images/en-us_image_0000001373288677.png
