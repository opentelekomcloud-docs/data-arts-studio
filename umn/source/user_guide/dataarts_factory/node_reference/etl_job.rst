:original_name: dataartsstudio_01_0461.html

.. _dataartsstudio_01_0461:

ETL Job
=======

Functions
---------

The ETL Job node is used to extract data from a specified data source, preprocess the data, and import the data to the target data source.

.. note::

   The destination is the ETL Job node of DWS and does not support scheduling using an agency. You are advised to use a public IAM account with better compatibility for scheduling. For details, see :ref:`Configuring a Scheduling Identity <dataartsstudio_01_0555>`.

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

   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                      | Mandatory             | Description                                                                                                                                                                                                              |
   +================================================================+=======================+==========================================================================================================================================================================================================================+
   | Max. Node Execution Duration                                   | Yes                   | Execution timeout interval for the node. If retry is configured and the execution is not complete within the timeout interval, the node will be executed again.                                                          |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Retry upon Failure                                             | Yes                   | Whether to re-execute a node if it fails to be executed. Possible values:                                                                                                                                                |
   |                                                                |                       |                                                                                                                                                                                                                          |
   |                                                                |                       | -  **Yes**: The node will be re-executed, and the following parameters must be configured:                                                                                                                               |
   |                                                                |                       |                                                                                                                                                                                                                          |
   |                                                                |                       |    -  **Retry upon Timeout**                                                                                                                                                                                             |
   |                                                                |                       |    -  **Maximum Retries**                                                                                                                                                                                                |
   |                                                                |                       |    -  **Retry Interval (seconds)**                                                                                                                                                                                       |
   |                                                                |                       |                                                                                                                                                                                                                          |
   |                                                                |                       | -  **No**: The node will not be re-executed. This is the default setting.                                                                                                                                                |
   |                                                                |                       |                                                                                                                                                                                                                          |
   |                                                                |                       |    .. note::                                                                                                                                                                                                             |
   |                                                                |                       |                                                                                                                                                                                                                          |
   |                                                                |                       |       If retry is configured for a job node and the timeout duration is configured, the system allows you to retry a node when the node execution times out.                                                             |
   |                                                                |                       |                                                                                                                                                                                                                          |
   |                                                                |                       |       If a node is not re-executed when it fails upon timeout, you can go to the **Default Configuration** page to modify this policy.                                                                                   |
   |                                                                |                       |                                                                                                                                                                                                                          |
   |                                                                |                       |       **Retry upon Timeout** is displayed only when **Retry upon Failure** is set to **Yes**.                                                                                                                            |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Policy for Handling Subsequent Nodes If the Current Node Fails | Yes                   | Operation that will be performed if the node fails to be executed. Possible values:                                                                                                                                      |
   |                                                                |                       |                                                                                                                                                                                                                          |
   |                                                                |                       | -  **Suspend execution plans of the subsequent nodes**: stops running subsequent nodes. The job instance status is **Failed**.                                                                                           |
   |                                                                |                       | -  **End the current job execution plan**: stops running the current job. The job instance status is **Failed**.                                                                                                         |
   |                                                                |                       | -  **Go to the next node**: ignores the execution failure of the current node. The job instance status is **Failure ignored**.                                                                                           |
   |                                                                |                       | -  **Suspend the current job execution plan**: If the current job instance is in abnormal state, the subsequent nodes of this node and the subsequent job instances that depend on the current job are in waiting state. |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Enable Dry Run                                                 | No                    | If you select this option, the node will not be executed, and a success message will be returned.                                                                                                                        |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0461__en-us_topic_0114569494_table987664914213:

.. table:: **Table 3** Lineage

   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Description                                                                                                                                                 |
   +==============+=============================================================================================================================================================+
   | **Input**    |                                                                                                                                                             |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add          | Click **Add**. In the **Type** drop-down list, select the type to be created. The value can be **DWS**, **OBS**, **CSS**, **HIVE**, **DLI**, or **CUSTOM**. |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK           | Click **OK** to save the parameter settings.                                                                                                                |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel       | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify       | Click |image8| to modify the parameter settings. After the modification, save the settings.                                                                 |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete       | Click |image9| to delete the parameter settings.                                                                                                            |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details | Click |image10| to view details about the table created based on the input lineage.                                                                         |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Output**   |                                                                                                                                                             |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add          | Click **Add**. In the **Type** drop-down list, select the type to be created. The value can be **DWS**, **OBS**, **CSS**, **HIVE**, **DLI**, or **CUSTOM**. |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK           | Click **OK** to save the parameter settings.                                                                                                                |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel       | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify       | Click |image11| to modify the parameter settings. After the modification, save the settings.                                                                |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete       | Click |image12| to delete the parameter settings.                                                                                                           |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details | Click |image13| to view details about the table created based on the output lineage.                                                                        |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002270846450.png
.. |image2| image:: /_static/images/en-us_image_0000002305406273.png
.. |image3| image:: /_static/images/en-us_image_0000002270846402.png
.. |image4| image:: /_static/images/en-us_image_0000002305439325.png
.. |image5| image:: /_static/images/en-us_image_0000002270846374.png
.. |image6| image:: /_static/images/en-us_image_0000002305439377.png
.. |image7| image:: /_static/images/en-us_image_0000002270846370.png
.. |image8| image:: /_static/images/en-us_image_0000002305406273.png
.. |image9| image:: /_static/images/en-us_image_0000002270846402.png
.. |image10| image:: /_static/images/en-us_image_0000002305439325.png
.. |image11| image:: /_static/images/en-us_image_0000002270846374.png
.. |image12| image:: /_static/images/en-us_image_0000002305439377.png
.. |image13| image:: /_static/images/en-us_image_0000002270846370.png
